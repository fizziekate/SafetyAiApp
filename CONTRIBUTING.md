# Contributing to SafetyAIApp

Thanks for your interest in contributing!

## Prerequisites
- JDK 17
- Android SDK (sdk.dir set in local.properties)
- Device/emulator for install/instrumented tests

## Build and run
- Assemble debug: `./gradlew :app:assembleDebug`
- Install debug: `./gradlew :app:installDebug`
- Launch: `adb shell am start -n com.felicity.safety/.MainActivity`

## Tests
- Unit tests (debug): `./gradlew :app:testDebugUnitTest`
- Instrumented tests: `./gradlew :app:connectedDebugAndroidTest`
- Single test: `./gradlew :app:testDebugUnitTest --tests "com.felicity.safety.YourTestClass[.method]"`

## Code style and static analysis
- Ktlint check/format: `./gradlew :app:ktlintCheck [:app:ktlintFormat]`
- Detekt: `./gradlew :app:detekt`
- Android Lint: `./gradlew :app:lintDebug`
- Run all checks: `./gradlew :app:assembleDebug :app:testDebugUnitTest :app:lintDebug :app:ktlintCheck :app:detekt`

## Commit messages
Use Conventional Commits where possible (e.g., `feat: ...`, `fix: ...`, `docs: ...`, `build: ...`, `ci: ...`, `style: ...`).

## Pull requests
- Keep PRs focused and small; include screenshots for UI changes.
- Ensure all checks pass locally and in CI.
- Link related issues (e.g., `Fixes #123`).

## Releases
Maintainers cut releases using tags (e.g., `v0.1.0`). The release workflow builds APK/AAB and attaches them to the GitHub Release.
