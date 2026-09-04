# LocaleRail Data Handling and Security

**Enterprise TranslationOps by StateRails.**

[Back to the LocaleRail README](../README.md) · [Download official releases](https://github.com/staterails/LocaleRail-Releases/releases)

This page provides a public, high-level summary for LocaleRail users. Consult the legal, privacy, and security documentation included with the installed application for terms and version-specific details.

## Salesforce localization data

LocaleRail processes Salesforce localization files that a user selects, including STF and supported XLIFF inputs. Those files, LocaleRail project workspaces, and generated translation artifacts can contain organization-specific source text, translated text, metadata, and identifiers.

Store and share those materials according to your organization's access-control, data-classification, retention, backup, and Salesforce deployment policies. Review generated artifacts before importing or distributing them.

## Optional Google Translation API workflow

LocaleRail provides both manual translation workflows and an optional Google Translation API workflow. When a user configures and runs the Google workflow, text selected for translation is sent to Google's service. Your organization is responsible for determining whether that use is appropriate and for complying with the applicable Google account, data-processing, and service terms.

## Credentials and public support

Treat Google Translation API credentials, Salesforce credentials, and other authentication material as secrets. Do not place credentials in translation source files, commit them to this repository, include them in screenshots, or post them in GitHub Issues or Discussions.

Before sharing logs, diagnostics, examples, or support bundles, review them and remove confidential source text, customer data, organization identifiers, file-system details, and credentials. Use only an established private StateRails business channel for material that cannot be disclosed publicly.

## Downloads and updates

Download LocaleRail only from the [official LocaleRail GitHub Releases page](https://github.com/staterails/LocaleRail-Releases/releases). The repository contains public installer and updater assets, but it does not contain LocaleRail's proprietary source code.

Release asset names and update metadata can be compatibility-sensitive. Users and contributors should not rename, rewrite, or republish those files.

## Licensing

LocaleRail is proprietary software developed by StateRails. Distribution and use are governed by the license included with the application. This release repository does not grant an open-source license. Source code is maintained privately and is not distributed here.

---

[Back to the LocaleRail README](../README.md) · [Product overview](PRODUCT_OVERVIEW.md) · [Installation guide](INSTALLATION.md) · [Official releases](https://github.com/staterails/LocaleRail-Releases/releases)
