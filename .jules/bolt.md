## 2024-05-24 - CoreFoundation memory leaks
**Learning:** This codebase does not use ARC for CoreFoundation. If you create objects containing "Create" or "Copy" in the function name (like `CFDictionaryCreate` or `CFDictionaryCreateMutable`), you must manually call `CFRelease()` to free memory and prevent leaks.
**Action:** Always verify `CFRelease()` pairs with CF creation/copy functions.
## 2024-05-24 - Linux compilation failure
**Learning:** This project targets iOS and relies on `xcrun` and the iOS SDK (`iphoneos`). Standard Linux environments will fail to compile the codebase without the SDK, making it impossible to verify the build properly using the `xcrun` command found in the README.
**Action:** Ensure that compilation failure in this environment is expected and rely on static analysis to verify code changes when working in standard environments without the SDK.
