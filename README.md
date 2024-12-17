<div align="center">

# 🚀 Ship capacitor apps

</div>

This repository contains reusable GitHub Actions workflows designed to simplify and standardize the delivery process of native mobile applications. These workflows are tailored for apps built with Capacitor and Svelte, using `pnpm` as the package manager. They support common deployment tasks such as publishing Android apps to the Google Play Store, submitting iOS apps to the App Store or TestFlight, and distributing builds via Firebase.

---

<br><br>

<div id="toc">


## 🚩 Table of Contents
- [🎯Purpose](#-purpose)
- [📂 Repository Structure](#-repository-structure)
- [🔑 Key Components](#-key-components)
- [🤯 Additional Requirements](#-additional-requirements)
- [👷🏼‍♀️ Available Workflows](#-available-workflows)
- [🧭 Usage](#-usage)
- [🙊 Secrets](#-secrets)
- [♻️ Examples](#-examples)

</div>

***


## 🎯 Purpose
The main goal of this repository is to provide a centralized and reusable solution for app delivery pipelines within your organization. By using the workflows defined here, you can ensure consistency, reduce repetitive configuration, and accelerate your deployment processes.

**[🔝 back to top](#toc)**

***

## 📂 Repository Structure

```
.
├── .github
│   └── workflows
│       ├── ship_android.yml
│       └── ship_ios.yml
├── examples
│   ├── publish_android_alpha_version.yml
│   ├── publish_android_beta_version.yml
│   ├── publish_android_production.yml
│   ├── publish_firebase_distribution.yml
│   ├── publish_ios_production.yml
│   └── publish_testflight.yml
└── fastlane
    ├── Fastfile
    └── Pluginfile
```

### 🔑 Key Components
- **`.github/workflows/`**: Contains reusable workflows for Android and iOS app delivery.
- **`examples/`**: This directory contains sample usage files to demonstrate how to configure and use the workflows in various deployment scenarios.
- **`fastlane/`**: This directory contains the `Fastfile` and `Pluginfile` required for managing Fastlane lanes and plugins used by the workflows. The `Fastfile` and `Pluginfile` are automatically copied into your project’s `fastlane` folder by the workflows.

### 🤯 Additional Requirements
You need to have a `Gemfile` in the root of your project with the following content:

```
source "https://rubygems.org"

gem 'fastlane'

plugins_path = File.join(File.dirname(__FILE__), 'fastlane', 'Pluginfile')
eval_gemfile(plugins_path) if File.exist?(plugins_path)
```

Additionally, ensure you have the `fastlane/metadata/android` and `fastlane/metadata/ios` folders set up for production deployments. Refer to the [Fastlane documentation](https://docs.fastlane.tools/) for detailed guidance on metadata setup.

**[🔝 back to top](#toc)**

***

## 👷🏼‍♀️ Available Workflows

### 🤖 Android Workflows
- **Publishing to the Google Play Store**
  - Alpha, Beta, and Production lanes are supported.
- **Distributing via Firebase App Distribution**

### 🍎 iOS Workflows
- **Submitting to the App Store**
  - Production submissions.
- **Publishing to TestFlight**

**[🔝 back to top](#toc)**

***

## 🧭 Usage

To use the workflows, reference them in your project’s GitHub Actions configuration files. Examples for each use case are provided in the `examples/` directory.

### Input Variables
The workflows require specific input variables (`with:`) for customization:
- **`backend-url`**: The backend URL used in your application.
- **`lane`**: The Fastlane lane to execute (e.g., `production`, `alpha`, `testflight`).
- Any additional required environment-specific variables (e.g., `DEMO_USER`, `DEMO_PASSWORD`).

### 🙊 Secrets
The workflows rely on secrets stored in your GitHub repository for sensitive information. Ensure the following secrets are configured before running the workflows:

#### 🤖 Android Secrets
- **`keystore-file`**: Base64-encoded keystore file.
- **`service-account`**: Service account JSON for Google Play Store API.
- **`keystore-alias`**: Keystore alias.
- **`keystore-password`**: Keystore password.
- **`keystore-key-password`**: Key password.
- **`firebase-app-id`** (for Firebase distributions).

#### 🍏 iOS Secrets
- **`APP_STORE_CONNECT_TEAM_ID`**: App Store Connect team identifier.
- **`BUNDLE_IDENTIFIER`**: App bundle identifier.
- **`BUILD_CERTIFICATE_BASE64`**: Base64-encoded iOS build certificate.
- **`BUILD_PROVISION_PROFILE_BASE64`**: Base64-encoded provisioning profile.
- **`APPLE_KEY_ID`**: Apple Developer Key ID.
- **`APPLE_ISSUER_ID`**: Apple Developer Issuer ID.
- **`APPLE_KEY_CONTENT`**: Apple private key content.
- **`APPLE_PROFILE_NAME`**: Provisioning profile name.
- **`P12_PASSWORD`**: Password for the .p12 certificate.

**[🔝 back to top](#toc)**

***

## ♻️ Examples

For detailed examples, refer to the `examples/` directory. Each example demonstrates the required configuration, input variables, and secrets for specific workflows, such as:
- Publishing Android apps in various release channels.
- Distributing iOS apps to TestFlight or the App Store.
- Deploying apps via Firebase.

**[🔝 back to top](#toc)**

***

## 📦 Setting Up


1. Clone this repository into your organization’s GitHub account.
2. Add the required secrets to your GitHub repository settings.
3. Reference the reusable workflows in your project’s GitHub Actions files.
4. Adjust input variables and secrets according to your deployment needs.

**[🔝 back to top](#toc)**
