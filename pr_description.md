⚡ Bolt: Replace CFDictionaryCreateMutable with CFDictionaryCreate

💡 What: Replaced usages of `CFDictionaryCreateMutable` followed by `CFDictionarySetValue` with direct `CFDictionaryCreate` using statically allocated C arrays for single-element dictionaries in `house_arrest.m`.

🎯 Why: In `send_error` and `handle_vending`, dictionaries are created with a single, known key-value pair and are immediately consumed and released. Allocating a mutable dictionary and then using a separate function call to insert an item introduces unnecessary memory overhead and runtime performance cost compared to a single static allocation and creation call.

📊 Impact: Minor reduction in CPU cycles and memory allocations during socket event handling and error reporting. Reduces CoreFoundation allocation overhead slightly on every handled command.

🔬 Measurement: Reviewing the memory footprint and profiling execution time under high message throughput would show slightly lower memory churn.
