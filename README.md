# 🔍 Memory-Mapped File Keyword Search in C

## 📌 Overview
This project demonstrates how to use **memory-mapped files (`mmap`)** in C to search for a keyword inside a file without loading the entire file into memory at once.  
Instead, the file is mapped into the process’s **virtual address space**, and the OS loads data **on-demand (page-by-page)** when accessed.

---

## ✨ Features
- Uses **low-level OS support (`mmap`)** for efficient file access.
- Searches for a **keyword** inside large files.
- Reports:
  - The **byte offsets** where matches occur.
  - The **total number of matches**.
- Works efficiently even for very large files (e.g., GBs).

---

---

## ⚙️ How Memory-Mapped Search Works
1. `mmap()` maps the file into the process’s **virtual memory space**.  
   - No data is copied upfront.
   - File looks like a big array of bytes (`file_data[0..size-1]`).

2. When your program accesses a portion of the file:
   - If it’s not in RAM → **page fault occurs**.
   - OS loads the corresponding **4 KB page** from disk into memory.
   - Access continues as if it was in normal memory.

3. This allows **lazy loading**:
   - Only the needed parts of the file are loaded.
   - Reduces memory overhead.

---
