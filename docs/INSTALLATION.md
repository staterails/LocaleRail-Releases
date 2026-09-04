# Installing LocaleRail

**Enterprise TranslationOps by StateRails.**

[Back to the LocaleRail README](../README.md) · [Download official releases](https://github.com/staterails/LocaleRail-Releases/releases)

## Supported platform

LocaleRail is released as a Windows desktop application. Consult the notes for the release you intend to install for any version-specific compatibility information.

## Download the latest stable release

1. Open the [official LocaleRail GitHub Releases page](https://github.com/staterails/LocaleRail-Releases/releases).
2. Select the latest stable release. Avoid prereleases unless you intentionally want a preview build.
3. Expand **Assets** if the files are not already visible.
4. Download `StateRails.LocaleRail.App-win-Setup.exe` for the normal Windows installation.

Do not use GitHub Actions workflow artifacts as the normal distribution channel. A portable ZIP may also be available for releases that support it, but the setup executable is the standard choice for most users.

## Install

1. Close any existing LocaleRail instance after saving your work.
2. Run the downloaded setup executable.
3. Follow the Windows installation prompts.
4. Start LocaleRail and use **Help → About** to confirm the installed version.

Retain your original Salesforce exports and follow your organization's normal backup and change-management practices for production localization work.

## Upgrade

Existing users should normally use LocaleRail's built-in update workflow. LocaleRail coordinates supported updates through the official GitHub Releases channel. If a release note provides different upgrade guidance, follow that release-specific guidance.

Do not rename downloaded update packages or edit release-feed files. Their names and metadata may be required by the updater.

## Report a problem

Use [GitHub Issues](https://github.com/staterails/LocaleRail-Releases/issues) for public installation and release problems. Include the LocaleRail version, Windows version, expected behavior, observed behavior, and reproducible steps.

Never attach API keys, credentials, private Salesforce exports, customer data, signing information, or other confidential material to a public issue.

## Related documentation

- [LocaleRail product overview](PRODUCT_OVERVIEW.md)
- [LocaleRail user guide](USER_GUIDE.md)
- [Data Handling and Security](DATA_HANDLING_AND_SECURITY.md)
- [Official releases and release notes](https://github.com/staterails/LocaleRail-Releases/releases)
