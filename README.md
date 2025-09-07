
ANAGRAM UNSCRAMBLER

# Anagram Unscrambler (Student Version)
**Author:** Rubben Shisso • **Student No:** ST10345300

A small **C# console app** that **unscrambles an English word** by finding **all valid anagrams** from a dictionary.  
Optimized with the right **data structures** and written to be clear for student projects and marking.

---

## ✅ Learning Goals
- Practice **hash maps** (`Dictionary<TKey, TValue>`) and **lists**.
- Implement an **anagram signature** and build an **inverted index**.
- Reason about **time/space complexity** and input **sanitization**.

---

## 🧠 How It Works (Algorithm)
Two words are anagrams if their **sorted lowercase letters** match. Example:  
`listen → eilnst`, `silent → eilnst` → **same signature**.

1. **Preprocess dictionary**: for each word, compute its **signature** and store it in  
   `Dictionary<string, List<string>> index` mapping `signature → [words...]`.
2. **Unscramble**: for an input word, compute its signature and **lookup** the list:
   - If found → print **all** matches (sorted, unique, case-insensitive).
   - If not found → print “No matches found.”

**Signature function**: `lowercase + sort letters`  
(Alternative: a **26-length frequency vector** for a–z to avoid sorting; see Extensions.)

---

## 🧰 Data Structures (and why)
- `Dictionary<string, List<string>>` → **O(1)** average lookup by signature.
- `List<string>` per key → store **all** anagrams for that signature.
- `string` signature → easy to compute and compare; stable for grading and demos.

---

## ⏱️ Complexity
- **Build index:** O(T log M) where T = total letters across the dictionary, M = max word length (for sorting).
- **Single query:** O(k log k) to sort the input letters (k = length) + O(1) map lookup.
- **Space:** O(N) words stored (plus small overhead for nodes/strings).

---
## 🧪 Try These Examples
- Input: `tinsel` → `enlist, inlets, listen, silent, tinsel`
- Input: `tones` → `notes, onset, stone, tones`
- Input: `alert` → `alter, later, alert`

> The app removes non-letters before processing (e.g., spaces, digits, punctuation).

---

## ▶️ How to Run

### Option A — Terminal
```bash
dotnet new console -n AnagramUnscrambler
cd AnagramUnscrambler

# Replace Program.cs with the code from this project (with your details already added)
dotnet run
```

### Option B — Visual Studio
1. **File → New → Project → Console App (.NET)**
2. Name: `AnagramUnscrambler` → **Create**
3. Replace **Program.cs** with the provided code.
4. Press **F5** to run.

---

## 🧯 Common Issues & Fixes
- **`dotnet` not recognized** → Install the .NET SDK and restart the terminal/PC.
- **No matches, just “?” or nothing** → Ensure your `words.txt` contains real words (letters only) and that your input is a shuffled word that exists in the list.
- **Large dictionary is slow** → See **Extensions** below for the frequency-vector signature.

---

## 🧩 Extensions (Optional)
- **Faster signature (O(k))**: use a **26-int frequency vector** instead of sorting; build a custom hash key (e.g., `"a1#b0#c2#..."`) or a struct with `GetHashCode/Equals`.
- **Sub-anagrams**: allow matches that use a **subset** of letters (input has leftovers).
- **GUI**: build a **Windows Forms** front end with a textbox and live results.
- **Unit tests**: add quick checks for `Signature`, `BuildAnagramIndex`, and edge cases.

---

## 📝 Submission Tips
Include in your submission:
1. **Program.cs** (single file).
2. **Screenshots** of the console showing at least **two** successful unscrambles.
3. A short paragraph (3–5 lines) explaining:
   - Why a **hash map** + **signature** was chosen,
   - What the **signature** is,
   - The **complexity** of build and query.

---

## 📜 Student Tag
This project prints the student tag at startup:
```
ANAGRAM UNSCRAMBLER 
Student: Rubben Shisso  |  No: ST10345300
```

---

## 🔒 License / Author
- **Author:** Rubben Shisso (ST10345300)
