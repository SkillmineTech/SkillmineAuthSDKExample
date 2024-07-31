## SkillmineAuthSDKExample
This repository provides an example of integrating the SkillmineAuthSDK into an Android application. The SkillmineAuthSDK simplifies the process of adding authentication features to your app

## Prerequisites

Ensure you have the following before starting:

- Android Studio installed.
- An existing Android project.
- Minimum SDK version 21 or higher.
- Internet permission in your `AndroidManifest.xml` file:
  ```xml
  <uses-permission android:name="android.permission.INTERNET" />

# SkillmineAuth Library

## Installation

Add it to your root settings.gradle.kts :

```gradle
dependencyResolutionManagement {
    repositoriesMode.set(RepositoriesMode.FAIL_ON_PROJECT_REPOS)
    repositories {
        google()
        mavenCentral()
        maven {url = uri("https://jitpack.io")}
    }
}

```

To use the SkillmineAuthSDK library, add it to your project dependencies. Open your build.gradle file (Module: app) and add the following:

```gradle
## auth_web_version = "1.0.6"
implementation "com.github.SkillmineTech:SkillmineAuthSDK:${auth_web_version}

```
Sync your project to download and include the dependency.

## Authentication Flow

```gradle
// Define the BASE_URL and CLIENT_ID
const val BASE_URL = "base_url"
const val CLIENT_ID = "client_id"
const val REDIRECT_URL = "redirect_url"
```
To initiate the authentication process, you can create an intent to open the Authentication Activity provided by the library. 
```
loginButton.setOnClickListener {
    val intent =
                AuthenticationActivity.createIntent(this, BASE_URL, CLIENT_ID, REDIRECT_URL)
            authActivityResultLauncher.launch(intent)
}
```
You can use an ActivityResultLauncher to handle the authentication process results.

Define authActivityResultLauncher in the Activity
Here, we want to open the Authentication Activity from LoginActivity.
Initialize the authActivityResultLauncher:

```
val authActivityResultLauncher = registerForActivityResult(ActivityResultContracts.StartActivityForResult()) { result ->
    if (result.resultCode == Activity.RESULT_OK) {
        val data: Intent? = result.data
        // Handle the result here
        val accessToken = data?.getStringExtra("access_token")
        // Use the access token as needed
    }
}
```


Please refer to integrate the SkillmineAuthSDK:
https://github.com/SkillmineTech/SkillmineAuthSDK/blob/master/README.md
