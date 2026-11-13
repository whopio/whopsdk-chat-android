# Whop chat SDK for Android

Whop chat for Jetpack Compose apps: a chat view, a thread view, a DM list and search, with events, context menus and theming.

## Install

In `settings.gradle.kts`, add the SDK's repository and Mux's, which serves `com.mux.video:upload` for video uploads:

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://whopio.github.io/whopsdk-chat-android/") }
        maven {
            url = uri("https://muxinc.jfrog.io/artifactory/default-maven-release-local")
            content { includeGroup("com.mux.video") }
        }
    }
}
```

Then in the app module:

```kotlin
dependencies {
    implementation("com.whop:chat-sdk:0.1.2")
}
```

## Requirements

- **Build settings:** Kotlin 2.2 or newer (the SDK is compiled with Kotlin 2.3, and older compilers can't read its metadata), `compileSdk` 36 or newer, `minSdk` 26 or newer, and core library desugaring enabled with `com.android.tools:desugar_jdk_libs` 2.1.5 or newer. AGP fails the build without them (`checkAarMetadata` for compileSdk and desugaring, the manifest merger for minSdk).
- **Compose:** the views are Compose-only and were built against Compose BOM 2026.06.01, so Gradle resolves the app's Compose to at least those versions.
- **Hilt:** optional. The AAR leaves out Hilt's `hilt_aggregated_deps` classes, so a Hilt app doesn't pick up the SDK's internal modules.
- **R8:** the AAR ships its keep rules; the app adds nothing.
- **Lint:** the AAR includes chat's notification code, which the SDK never runs. Lint still flags `NotificationPermission` for an app targeting API 33 or newer that doesn't declare `android.permission.POST_NOTIFICATIONS`. Disable or baseline that check; declaring the permission only makes sense if the app sends notifications itself.
- **Resources:** the SDK's resources aren't prefixed. An app resource with the same name (for example `ic_whop_logo_24`) replaces the SDK's.
