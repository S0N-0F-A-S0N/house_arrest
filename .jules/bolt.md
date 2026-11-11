## 2024-11-11 - Optimize Dictionary Allocation and Fix Memory Leaks
**Learning:** Found that CoreFoundation mutable dictionaries were being created only to be populated once and sent. Also noticed that memory wasn't being correctly managed using CFRelease in all code paths causing a memory leak.
**Action:** Replace `CFDictionaryCreateMutable` and `CFDictionarySetValue` with `CFDictionaryCreate` providing C-arrays for keys/values for single-pass allocations, and always verify all `CFRelease` paths when allocating CoreFoundation objects manually.
