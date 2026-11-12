# NSDK for Android

The Niantic Spatial SDK (NSDK) for Android, distributed as an AAR through a Maven
repository hosted in this repository. It provides native integration for AR features such
as meshing, occlusion, object detection, localization, and more.

## Quick Links
* [NSDK API Reference](https://www.nianticspatial.com/docs/api/kotlin/)
* [Documentation](https://www.nianticspatial.com/docs/nsdk/?platform=kotlin)
* [Niantic Spatial Platform](https://www.nianticspatial.com)

## Requirements

* `minSdk` 24 or higher
* `compileSdk` 35 or higher
* Java 11 source and target compatibility
* Gradle 8.11 or later

## Getting Started

### 1. Add the NSDK Maven repository

Artifacts are served per release line, so the URL names the line you are building against:
`nsdk-4.3-release` for any 4.3.x release, `nsdk-4.4-release` for any 4.4.x, and so on.

In `settings.gradle.kts`:

```kotlin
dependencyResolutionManagement {
    repositories {
        google()
        mavenCentral()
        maven { url = uri("https://raw.githubusercontent.com/nianticspatial/nsdk-library-aar/nsdk-MAJOR.MINOR-release") }
    }
}
```

`main` follows the latest release, but can lag behind it for a while after a new release
ships, and it does not serve older lines. Use the release-line URL above.

### 2. Declare the dependency

In your module's `build.gradle.kts`:

```kotlin
dependencies {
    implementation("com.nianticspatial:nsdk:VERSION")
}
```

Replace `VERSION` with the release you want, from the line named in the URL above. The
versions available on that line are listed in
[`com/nianticspatial/nsdk/maven-metadata.xml`](com/nianticspatial/nsdk/maven-metadata.xml).

Every release of a line stays available on that line's branch — Gradle resolves these
artifacts by URL rather than by git tag, so a version you depend on is never removed from
its line. A release tag (for example `4.3.2`) also works as a URL ref, if you would rather
pin to an immutable snapshot than track the line.

## Versioning

Releases follow SemVer 2.0. A version containing a hyphen — for example
`4.3.0-25081200` — is a prerelease.

Pin an **exact version**. Gradle's version ranges and `latest.release` exclude prereleases,
so a range will not resolve one.

## License

See [LICENSE](LICENSE).
