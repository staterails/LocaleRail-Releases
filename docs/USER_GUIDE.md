# LocaleRail User Guide

**LocaleRail**  
**Enterprise TranslationOps by StateRails**

LocaleRail helps you prepare Salesforce translation data, run Google Translation API automation, and generate validated import-ready STF output.

---

## Table of Contents

1. [What LocaleRail Does](#what-localerail-does)
2. [Supported Workflow](#supported-workflow)
3. [Prerequisites](#prerequisites)
4. [Install and Update](#install-and-update)
5. [Application Overview](#application-overview)
6. [Step 1 — Source](#step-1--source)
7. [Step 2 — Workspace](#step-2--workspace)
8. [Step 3 — Translate](#step-3--translate)
9. [Step 4 — Review & Output](#step-4--review--output)
10. [Tracking, Cache, and API Usage](#tracking-cache-and-api-usage)
11. [Common Messages](#common-messages)
12. [Troubleshooting](#troubleshooting)
13. [Best Practices](#best-practices)

---

## What LocaleRail Does

LocaleRail provides a structured translation workflow for Salesforce translation files:

- Reads **Salesforce STF** source files
- Uses a matching **Salesforce XLF** export as the authoritative length reference
- Creates a reusable **workspace**
- Supports **sample translation** before full runs
- Uses **Google Translation API**
- Tracks progress, cache reuse, requests, and character consumption
- Produces a validated translation result set for final STF generation

---

## Supported Workflow

LocaleRail follows a 4-step workflow:

1. **Source**  
   Choose the STF and XLF source files and prepare the workspace.

2. **Workspace**  
   Review workspace details such as language, entries, chunks, and length validation.

3. **Translate**  
   Run a sample translation or full translation using the Google Translation API.

4. **Review_Output**  
   Review translated output and generate the final validated Salesforce STF.

---

## Prerequisites

Before using LocaleRail, ensure the following are available:

- A valid **Salesforce STF** source file
- A matching **Salesforce XLF** export for the same target language and metadata scope
- A valid **Google Translation API key**
- Internet access for Google Translation API calls
- Permission to read/write files in your selected workspace folder

### Important notes

- The **XLF file is required** because LocaleRail uses Salesforce length metadata to enforce exact translation width validation.
- The source STF and XLF should correspond to the same language and extraction scope.
- LocaleRail stores application data in a persistent user location and is not temp-folder based.

---

## Install and Update

LocaleRail is distributed as a Windows application with self-update support through GitHub Releases.

### Verify installed version

Use **Help → About** to verify:

- Product name
- Version
- Source repository
- Update repository
- Persistent app data path
- Default workspace path

![About LocaleRail v1.1.0](images/user-guide/01-about-v1.1.0.png)

---

## Application Overview

The application header displays the current workflow using a path-style progress component:

- **Blue** = current active step
- **Green** = completed step
- **Gray** = upcoming step

This makes it easy to understand where you are in the end-to-end translation process.

---

## Step 1 — Source

In **Step 1**, provide:

- **Source STF**
- **Length reference** (Salesforce XLF)
- **Workspace parent**
- **Entries per chunk**

The chunk size defaults to **1,000**, but LocaleRail allows any valid value from **1** up to the total translation-entry count of the selected STF.

### What happens in this step

When you click **Create Workspace + TXT Chunks**, LocaleRail:

- parses the STF
- counts entries
- validates the XLF length metadata
- creates a workspace
- builds chunk files for processing

### Example

In the example below:

- the STF contains **36,019** entries
- the default chunk size remains **1,000**
- the maximum allowed chunk size is the total STF entry count

![Step 1 - Source parsing](images/user-guide/02-step1-source-parsing.png)

### Notes

- If your STF contains fewer than 1,000 entries, the effective initial value is clamped accordingly.
- Chunk files are primarily for workflow organization, audit, and fallback/manual inspection.

---

## Step 2 — Workspace

Once parsing completes successfully, LocaleRail creates the workspace and moves you to **Step 2**.

The workspace screen shows:

- target language
- total entries
- chunk size
- chunk count
- length validation status

You can also use **Load Existing Workspace...** to reopen a previously created workspace.

### Example

Below, the workspace was created successfully with:

- **Entries:** 36,019
- **Chunks:** 37
- **Exact length limits:** 36,019 / 36,019

![Step 2 - Workspace ready](images/user-guide/04-step2-workspace-ready.png)

### Workspace folder structure

LocaleRail creates structured folders for the translation lifecycle, including:

- source chunks
- translated results
- tracking/progress files

The message shown after workspace creation confirms that:

- source chunks are stored in **`01_Source_Chunks`**
- translated results will be generated into **`02_Translated_Results`**

---

## Step 3 — Translate

In **Step 3**, LocaleRail connects the prepared workspace to the Google Translation API.

The translation screen shows:

- API key status
- cache translation count
- tracked API character count
- target language details
- run mode controls
- progress and status details

![Step 3 - Translate sample mode](images/user-guide/05-step3-translate-sample-mode.png)

### Run modes

LocaleRail supports two run modes:

#### 1. Test / Sample
Use this first to validate:

- translation quality
- formatting behavior
- token preservation
- language direction and output expectations

#### 2. Full translation
Once satisfied with the sample, switch to full translation for the remaining dataset.

---

### Google API Settings

Use **Google API Settings...** to configure:

- Google Translation API key
- source language code
- API test target language code
- max strings per request
- max characters per request
- delay between requests
- retry limits
- timeout
- app-side throttle
- cache reuse behavior

### API key re-entry note

If LocaleRail cannot decrypt a previously stored key (for example after an identity/storage change or encryption-context change), it will prompt you to re-enter and save the API key again.

Example message:

![API key re-entry required](images/user-guide/03-api-key-reentry-required.png)

If you see this:

1. Open **Google API Settings**
2. Re-enter the API key
3. Click **Save**
4. Resume the workflow

---

### Running a sample translation

Sample mode is useful for validating translation behavior before processing a large dataset.

In the example below:

- sample size was **25** entries
- Google API translated **25** entries
- the result was stored and can be reused later in full mode

![Sample translation complete](images/user-guide/06-step3-sample-complete.png)

### Important sample-mode behavior

- Sample translations are saved
- Sample rows are reused later
- Those rows are **not translated again** during full mode

This reduces duplicate API consumption.

---

### Running a full translation

When switching to full mode, LocaleRail processes the remaining untranslated rows and shows live metrics such as:

- completed entries
- percent complete
- cache hits
- API-translated rows
- request count
- API characters sent
- characters avoided via cache/duplicate reuse

Example in-progress screen:

![Full translation in progress](images/user-guide/07-step3-full-translation-progress.png)

### Progress metrics explained

- **Completed**: total translated output rows completed so far
- **Cache**: rows reused from cache
- **API**: rows translated via the API during the current run
- **Requests**: number of Google API requests sent
- **API characters sent**: characters billed/sent to Google
- **Characters avoided by cache/duplicate reuse**: optimization achieved through reuse

---

## Step 4 — Review & Output

After translation is complete, proceed to **Step 4** to review output and generate the final Salesforce STF.

This step is intended for:

- reviewing completion state
- validating translated result readiness
- generating the final import-ready STF
- confirming the output can be used back in Salesforce

### Expected outcome

The final result should be a validated UTF-8 Salesforce import STF based on:

- the original source STF structure
- XLF-enforced field-length constraints
- translated output produced in the workspace

---

## Tracking, Cache, and API Usage

LocaleRail tracks translation activity to support reliability and efficiency.

### What is tracked

- successful API requests
- request counts
- character consumption
- cache reuse
- run progress
- resumable processing state

### Cache behavior

If enabled, LocaleRail reuses identical valid translations from the local cache to reduce repeated Google API usage.

This helps:

- lower API consumption
- reduce duplicate translation work
- speed up repeat or interrupted runs

### Tracking benefits

Tracking enables:

- safer long-running translation jobs
- better visibility into progress
- retry/backoff workflows
- run resumption after interruption

---

## Common Messages

### “Workspace created successfully.”
This means LocaleRail finished:

- STF parsing
- XLF validation
- workspace creation
- chunk generation

### “The stored Google Translation API key cannot be decrypted by this LocaleRail version.”
This means you need to:

- re-enter the API key
- click **Save**
- continue

### “Sample translation completed successfully.”
This confirms:

- sample rows were translated
- results were saved to `02_Translated_Results`
- sample rows will be reused later in full mode

---

## Troubleshooting

### 1. Workspace creation appears slow
Large STF files can take time to parse. LocaleRail shows progress while checking rows.

What to do:

- wait for parsing to complete
- avoid clicking the action button repeatedly
- verify the STF and XLF are correct if progress does not continue

---

### 2. API key is configured but translation cannot start
Check the following:

- the API key is valid
- the key is saved successfully
- Google Cloud Translation API is enabled in the Google project
- the workstation has internet access

If prompted, re-enter the key and save it again.

---

### 3. Translation output is rejected by Salesforce
Verify:

- the XLF reference matches the STF
- the target language is correct
- the imported STF is the final validated output from LocaleRail
- source/export scope was consistent between STF and XLF

---

### 4. Full translation seems slower than expected
Possible reasons:

- very large datasets
- throttle settings
- retry/backoff activity
- network latency
- Google API limits
- strict request-size configuration

Check:

- **delay between successful requests**
- **max strings per API request**
- **max characters per API request**
- **app character throttle / minute**

---

### 5. Why is chunk count different from expectations?
Chunk count is derived from:

- total entry count
- selected chunk size

Example:

- 36,019 entries
- chunk size 1,000
- chunk count 37

---

## Best Practices

### Use sample mode first
Always run a small sample before full translation, especially for:

- a new language
- a new metadata set
- a new API configuration
- a new translation prompt/expectation review

### Always use the correct XLF
The XLF file is critical because LocaleRail uses it for exact Salesforce length validation.

### Keep chunk size practical
The default of **1,000** is a good starting point. Adjust only if there is a specific operational need.

### Reuse cache where possible
Keep cache reuse enabled unless you intentionally need a fresh translation result set.

### Monitor tracked API usage
Use the displayed request and character metrics to understand usage trends and potential cost implications.

---

## Summary

LocaleRail provides a structured, controlled translation workflow:

1. **Select STF and XLF**
2. **Create workspace**
3. **Run sample translation**
4. **Run full translation**
5. **Generate final validated STF**

This approach helps ensure:

- Salesforce-safe length compliance
- reduced duplicate API consumption
- repeatable translation operations
- a more reliable translation release process

---

## Support / Repository Links

- **Source repository:** `https://github.com/staterails/LocaleRail`
- **Release repository:** `https://github.com/staterails/LocaleRail-Releases`

For release-specific notes, see the GitHub Release entry for your installed version.
