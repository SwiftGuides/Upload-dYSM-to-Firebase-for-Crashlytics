# Upload-dYSM-to-Firebase-for-Crashlytics
This is the guide to show where is dYSM Located and how to upload it.

Source :- https://stackoverflow.com/a/61653107/10422074

- Goto Build Phase/ Add new run Script
- Paste below code

#### if you are using Firebase Crashlytics SDK
```
if [[ "${CONFIGURATION}" = "Release" ]] || [[ "${CONFIGURATION}" = "Adhoc" ]]; then
  echo "Uploading dSYMs.."
  find "${DWARF_DSYM_FOLDER_PATH}" -name "*.dSYM" | xargs -I \{\} "${PODS_ROOT}/FirebaseCrashlytics/upload-symbols" -gsp "${SRCROOT}/GoogleService-Info.plist" -p ios \{\}
else
  echo "Skip dSYMs upload"
fi
```

#### if you are using Fabric SDK

```
if [[ "${CONFIGURATION}" = "Release" ]] || [[ "${CONFIGURATION}" = "Adhoc" ]]; then
  echo "Uploading dSYMs.."
  find "${DWARF_DSYM_FOLDER_PATH}" -name "*.dSYM" | xargs -I \{\} "${PODS_ROOT}/Fabric/upload-symbols" -gsp "${SRCROOT}/GoogleService-Info.plist" -p ios \{\}
else
  echo "Skip dSYMs upload"
fi
