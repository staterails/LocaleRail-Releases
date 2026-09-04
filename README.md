# LocaleRail

**Enterprise TranslationOps by StateRails.**

LocaleRail is a Windows desktop application for managing enterprise Salesforce localization and Translation Workbench workflows.

It helps Salesforce teams import, reconcile, translate, review, validate, and prepare large-volume localization files for deployment while maintaining a persistent project translation registry and translation history.

> This public repository hosts the official LocaleRail releases and update assets. LocaleRail is proprietary software; its source code is maintained separately in a private repository and is not distributed here.

## What is LocaleRail?

LocaleRail is designed for Salesforce teams working with large translation datasets and repeatable localization cycles. It supports Salesforce Translation Workbench workflows involving STF files and XLIFF files where supported, including source translations, Outdated and Untranslated exports, and bilingual translation exports.

Each target-language project maintains a Project Translation Registry so new Salesforce baselines can be reconciled with existing work. This allows teams to retain pending LocaleRail translations when source content or Salesforce translation values change, review conflicts, and use translation revision and history information supported by the current release.

LocaleRail combines manual translation, translation dictionary and reuse workflows, and optional Google Translation API processing. It provides translation validation before generating final Salesforce-compatible artifacts, giving enterprise translation management teams a structured TranslationOps workflow on Windows.

## Key capabilities

- Salesforce Translation Workbench STF workflows
- XLIFF import and validation workflows where supported
- Source STF and XLIFF import
- Outdated and Untranslated Salesforce translation import
- Bilingual Translation Workbench import
- Persistent Project Translation Registry
- Multiple target-language projects
- Translation reconciliation as Salesforce baselines change
- Preservation of pending LocaleRail manual and Google translations during reconciliation
- Manual translation workflow
- Optional Google Translation API workflow
- Translation dictionary, translation memory, and reuse
- Translation revision, history, and conflict review support
- Large translation dataset handling
- Validation before final output
- Final Salesforce-compatible translation artifacts
- Update management through official LocaleRail releases

## Official release repository

This repository is the official public download and update location for LocaleRail by StateRails. Release assets include the Windows installer and the metadata used by supported LocaleRail update flows. The proprietary application source is not part of this repository.

## Download LocaleRail

[Open the official LocaleRail GitHub Releases page](https://github.com/staterails/LocaleRail-Releases/releases).

Users should normally select the latest stable Windows release, expand its **Assets** section, and download `StateRails.LocaleRail.App-win-Setup.exe`. Use GitHub Releases—not workflow artifacts—as the normal distribution channel.

See the [installation guide](docs/INSTALLATION.md) for installation and upgrade guidance.

## Documentation

- [Product overview](docs/PRODUCT_OVERVIEW.md)
- [Installation and upgrades](docs/INSTALLATION.md)
- [User guide](docs/USER_GUIDE.md)
- [Data handling and security](docs/DATA_HANDLING_AND_SECURITY.md)
- [Release notes and downloads](https://github.com/staterails/LocaleRail-Releases/releases)
- [Support and issue reporting](https://github.com/staterails/LocaleRail-Releases/issues)

## Security and Data Handling

Salesforce localization files can contain organization-specific text and metadata. Handle input files, workspaces, generated artifacts, credentials, and diagnostic information according to your organization's security and retention requirements. The Google Translation API workflow is optional; when used, text selected for translation is sent to that service.

Read [Data Handling and Security](docs/DATA_HANDLING_AND_SECURITY.md) before processing sensitive localization material. Never include API keys, credentials, confidential source files, or customer data in a public GitHub issue.

## Licensing

LocaleRail is proprietary software developed by StateRails. Distribution and use are governed by the license included with the application. This release repository does not grant an open-source license. Source code is maintained privately and is not distributed through this repository.

## About StateRails

LocaleRail is developed by StateRails.

**Enterprise TranslationOps by StateRails.**
