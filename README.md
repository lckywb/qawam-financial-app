# QAWĀM Financial App

Qur'an-based personal financial decision support prototype using the Qawām framework.

## Included prototype features

- Onboarding
- Home Dashboard
- Financial Inventory
- Debt Register
- Income and expense recording
- "Saya Mau Membeli..."
- Qawām Decision Check
- Condition / Need / Purpose / Proportionality / Continuity checks
- Isrāf / Iqtār / Tabdhīr reasoning layer
- Decision results: Proporsional, Pertimbangkan, Tunda, Data Belum Cukup
- Decision history
- Local persistence with SharedPreferences
- GitHub Actions debug APK build

This is a decision-support prototype, not a fatwa engine.

## Architecture

The prototype keeps the Qur'anic framework separate from UI:
- QawamEngine.java = decision logic
- AppState.java = local financial state
- MainActivity.java = UI/navigation

## Build

Android Native / Java 17 / Gradle 8.7-compatible.
