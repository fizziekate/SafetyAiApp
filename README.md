# SafetyAIApp

Android app using Kotlin, Jetpack Compose, Hilt DI, WorkManager, and TensorFlow Lite.

Tech stack
- Kotlin + Gradle (Kotlin DSL)
- Jetpack Compose (Material 3)
- Hilt (2.52)
- WorkManager
- TensorFlow Lite (2.14.0) + Support (0.4.4)

Requirements
- JDK 17
- Android SDK (sdk.dir set in local.properties)
- A device/emulator for install/run or instrumented tests

Quickstart (terminal)
- Build: `./gradlew :app:assembleDebug`
- Install (device/emulator running): `./gradlew :app:installDebug`
- Launch: `adb shell am start -n com.felicity.safety/.MainActivity`
- Unit tests: `./gradlew :app:testDebugUnitTest`
- Instrumented tests: `./gradlew :app:connectedDebugAndroidTest`
- Lint: `./gradlew :app:lintDebug`

Notes
- Compose compiler extension is 1.5.11; this project pins Kotlin 1.9.23 per the Compose compatibility map.
- AGP 8.5.2, Gradle 8.7 via wrapper. Hilt plugin is 2.52; Hilt runtime/processor also 2.52.
- See WARP.md for a concise guide tailored to AI assistants.
