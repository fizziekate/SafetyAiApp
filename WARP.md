# WARP.md

This file provides guidance to WARP (warp.dev) when working with code in this repository.

Project overview
- Android app (Kotlin, Gradle Kotlin DSL) with Jetpack Compose UI, Hilt for dependency injection, WorkManager for background tasks, and TensorFlow Lite libraries for on-device ML inference.
- Single module: app (see `settings.gradle.kts`). Package/namespace: `com.felicity.safety`. Entry points: `SafetyAIApp` (Application annotated with `@HiltAndroidApp`) and `MainActivity` (Compose host).

Tooling and versions (from Gradle files)
- Gradle wrapper: 8.7; Android Gradle Plugin: 8.5.2; Kotlin: 1.9.23; Compose compiler extension: 1.5.11; Hilt plugin: 2.52.
- compileSdk/targetSdk: 34; minSdk: 26; Java/Kotlin target: 17.
- Version catalog: see `gradle/libs.versions.toml` for dependency and plugin versions.

Common commands (run from repo root)
- Gradle wrapper: use `./gradlew` (on Windows, `gradlew.bat`).
- Clean/build
  - Clean: `./gradlew clean`
  - Build all: `./gradlew build`
  - Assemble debug APK: `./gradlew :app:assembleDebug`
  - Assemble release APK: `./gradlew :app:assembleRelease`
  - Generate Play Store bundle: `./gradlew :app:bundleRelease`
- Install/run on device or emulator (device/emulator must be running and visible to `adb`)
  - Install debug build: `./gradlew :app:installDebug`
  - Launch app: `adb shell am start -n com.felicity.safety/.MainActivity`
- Lint
  - Lint (all variants): `./gradlew :app:lint`
  - Lint debug only: `./gradlew :app:lintDebug`
- Style and static analysis
  - Ktlint: `./gradlew :app:ktlintCheck` (format: `:app:ktlintFormat`)
  - Detekt: `./gradlew :app:detekt`
- Tests
  - JVM unit tests (debug): `./gradlew :app:testDebugUnitTest`
  - Instrumented tests (on device/emulator): `./gradlew :app:connectedDebugAndroidTest`
  - Run a single unit test class: `./gradlew :app:testDebugUnitTest --tests "com.felicity.safety.YourTestClass"`
  - Run a single unit test method: `./gradlew :app:testDebugUnitTest --tests "com.felicity.safety.YourTestClass.yourMethod"`

High-level architecture
- Application and DI: `SafetyAIApp` extends `Application` and is annotated with `@HiltAndroidApp`, enabling Hilt code generation. The Hilt Gradle plugin and `kapt` are applied in `app/build.gradle.kts`.
- UI layer: `MainActivity` sets a Compose content tree using Material 3. Compose libraries are version-aligned via the Compose BOM declared in dependencies.
- Background work: `androidx.work:work-runtime-ktx` is included to schedule background jobs; hook your workers into Hilt as needed.
- On-device ML: `tensorflow-lite` and `tensorflow-lite-support` dependencies are present for TensorFlow Lite inference.
- Build configuration: `app/build.gradle.kts` sets namespace, SDK levels, Java/Kotlin 17, enables Compose, configures `composeOptions`, and defines debug/release `buildTypes` with ProGuard rules (`proguard-android-optimize` + `proguard-rules.pro`).

Notes
- CI: `.github/workflows/ci.yml` runs assemble, unit tests, lint, ktlint, and detekt on pushes/PRs. Releases: `.github/workflows/release.yml` builds APK/AAB on tags.
- See `README.md` for quickstart and `CONTRIBUTING.md` for workflows. Adjust task qualifiers if modules/flavors are added (`:module:assemble<Variant>`).
