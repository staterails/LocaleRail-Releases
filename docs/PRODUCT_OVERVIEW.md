# LocaleRail Product Overview

**Enterprise TranslationOps by StateRails.**

[Back to the LocaleRail README](../README.md) · [Download official releases](https://github.com/staterails/LocaleRail-Releases/releases)

## Overview

LocaleRail is a Windows desktop application for enterprise Salesforce translation management. It provides a project-based TranslationOps workflow for importing, reconciling, translating, reviewing, validating, and preparing Salesforce localization files for deployment.

The application is intended for repeatable Salesforce Translation Workbench work involving STF and supported XLIFF files, multiple target languages, and datasets that are difficult to manage safely through one-off file editing. LocaleRail keeps translation work associated with a persistent project rather than treating each export as an unrelated batch.

## Why LocaleRail

Salesforce source content and translation baselines change over time. A new export can contain new source translations, revised labels, existing bilingual translation values, and entries classified as outdated or untranslated. Translation teams need to reconcile those changes without silently losing pending work.

LocaleRail provides a controlled path from source import to a validated final artifact. Its Project Translation Registry, dictionary and reuse features, manual and API-assisted workflows, and history support reduce repeated effort while keeping review and deployment preparation visible.

## Salesforce Translation Workbench Support

Current LocaleRail releases support Salesforce Translation Workbench STF workflows, including:

- Source STF import
- Outdated and Untranslated STF import
- Bilingual Translation Workbench import
- Source and target language checks
- Reconciliation of later Salesforce baselines
- Salesforce-compatible final STF output

LocaleRail also supports XLIFF import and validation workflows where available in the current release. File-purpose and language checks help identify mismatched inputs before they change a project.

## Translation Workflow

A typical LocaleRail workflow is:

1. Create or open a target-language project.
2. Import the applicable Salesforce STF or supported XLIFF files.
3. Reconcile the imported baseline with the Project Translation Registry.
4. Translate through the manual workflow, reuse sources, or the optional Google Translation API workflow.
5. Review pending work, changes, and conflicts.
6. Validate translations and formatting constraints.
7. Generate the final Salesforce-compatible translation artifact.

The exact screens and available actions can vary by release and file type. Consult the in-application help and the release notes for version-specific behavior.

## Project Translation Registry

The Project Translation Registry is the durable record of translation work for a LocaleRail project. It associates Salesforce keys and source text with known Salesforce values, pending LocaleRail values, translation status, and supported revision or history information.

When a later Salesforce baseline is imported, LocaleRail reconciles it with the registry. Pending manual or Google-assisted LocaleRail work can be preserved while changed baselines and genuine conflicts remain available for review. Separate projects support multiple target-language workflows.

## Translation Reuse and Dictionary

LocaleRail can reuse eligible translations from the Project Translation Registry, translation dictionary, and project translation memory before external translation is required. Reuse is constrained by the language and validation context so teams can reduce repeated translation effort without bypassing review.

Manual translation remains available. Teams that configure Google Translation API access can use the optional API-assisted workflow and then review and validate its results before output.

## Validation

LocaleRail validates translation content before final output. Depending on the input and current release, checks can cover language identity, required values, formatting tokens, length constraints, and readiness for Salesforce import.

Validation is a deployment-preparation aid, not a substitute for organizational review or Salesforce testing. Teams should review the generated artifact and validate it in their normal Salesforce deployment process.

## Large Project Support

LocaleRail is designed for large Salesforce localization datasets. Current releases include scalable import, registry, filtering, reconciliation, validation, and output paths so high-volume projects can be processed without relying on a single manual spreadsheet workflow.

## Security and Data Handling

LocaleRail processes Salesforce localization material selected by the user. Organizations remain responsible for classifying that material, controlling access to project workspaces and outputs, and deciding whether content is appropriate for an external translation service.

The Google Translation API workflow is optional. See [Data Handling and Security](DATA_HANDLING_AND_SECURITY.md) for public guidance, and consult the legal and security documentation included with the installed application for the applicable release.

## Releases and Updates

Official Windows installers, portable packages when provided, release notes, and updater assets are published on the [LocaleRail GitHub Releases page](https://github.com/staterails/LocaleRail-Releases/releases). Users should normally download the latest stable setup executable from that page. Existing installations can use LocaleRail's supported update workflow.

Release tags, asset names, package identifiers, and update metadata are compatibility-sensitive. Future human-facing release titles should follow this form:

> LocaleRail vX.Y.Z — Enterprise TranslationOps by StateRails

Release notes should identify LocaleRail, StateRails, Salesforce Translation Workbench relevance, major highlights, installer guidance, and links to the public documentation. Automated updater assets must remain separate and unchanged by documentation-only work.

## Licensing

LocaleRail is proprietary software developed by StateRails. Distribution and use are governed by the license included with the application. This public release repository does not grant an open-source license. The source code is maintained privately and is not distributed here.

## StateRails

LocaleRail is developed by StateRails.

**Enterprise TranslationOps by StateRails.**

---

[Back to the LocaleRail README](../README.md) · [Installation guide](INSTALLATION.md) · [Official releases](https://github.com/staterails/LocaleRail-Releases/releases)
