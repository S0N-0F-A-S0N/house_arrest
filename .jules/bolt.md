## 2024-11-11 - [Use CFDictionaryCreate instead of CFDictionaryCreateMutable for static dictionaries]
**Learning:** Using `CFDictionaryCreateMutable` and `CFDictionarySetValue` for a single-element dictionary that is immediately used and discarded is inefficient and causes unnecessary overhead compared to `CFDictionaryCreate` with static arrays.
**Action:** Always prefer `CFDictionaryCreate` with C arrays for small, statically-sized dictionaries in CoreFoundation to reduce memory allocation overhead and function call count.
