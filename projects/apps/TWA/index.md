Using TWA, you can serve your PWA web application to users as an Android app. Learn more about about this [here](https://developer.chrome.com/docs/android/trusted-web-activity/).


## Setup

### Install
We will be using [Bubblewrap](https://github.com/GoogleChromeLabs/bubblewrap) to generate our project. So first install it
```bash
npm i -g @bubblewrap/cli
```

### Directory
Create a directory to init
```bash
mkdir ownstore-app-twa
```

### Initialize
Now let's initialize our project with a manifest file. Using OwnStore's demo manifest as an example here.
```bash
bubblewrap init --manifest=https://own-store-demo.vercel.app/json/manifest.json
```

This command will install
- JDK 8 if not found. I had to say for this.
- Android SDK if not found. I had previously installed the SDK here: `/Users/faiyazshaikh/Library/Android/sdk`.

You will also be asked with a few questions.

### Build
Once the project is initialized, we can build and generate our APK. 
```bash
bubblewrap build 
```

You can also provide `----skipPwaValidation` to bypass PWA validation checks.

### Fingerprint
Next step is to generate SHA256 fingerprints. Run this command
```bash
keytool -printcert -jarfile app-release-signed.apk | grep SHA256
```

Copy the output.

### Web asset linking
Create a file named `/public/.well-known/assetlinks.json` in website project. This will be served as `/.well-known/assetlinks.json`. Paste the following content in this JSON file.
```json
[{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "app.own_store_demo.twa",
    "sha256_cert_fingerprints": [
      "<Paste SHA256 fingerprint here>"
    ]
  }
}]

```


Go through this [doc](https://developer.chrome.com/docs/android/trusted-web-activity/quick-start/) for more detailed instructions.
