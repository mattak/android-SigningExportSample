# android-SigningExportSample

This is android signing export sample.
Using `apply from`, signingConfigs can be export as external gradle file.

## Example

app/build.gradle

    android {
        // ...

        // signingConfigs
        apply from: 'signingConfigs/debug.gradle', to: android
        apply from: 'signingConfigs/release.gradle', to: android

        buildTypes {
            debug {
                debuggable true
                signingConfig signingConfigs.debug
            }

            release {
                minifyEnabled false
                proguardFiles getDefaultProguardFile('proguard-android.txt'), 'proguard-rules.pro'
                signingConfig signingConfigs.release
            }
        }
    }

app/signingConfigs/debug.gradle

    signingConfigs {
        debug {
            storeFile file("debug.keystore")
            storePassword "android"
            keyAlias "androiddebugkey"
            keyPassword "android"
        }
    }

