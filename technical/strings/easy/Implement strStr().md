---
attachments: [Clipboard_2021-04-12-08-49-54.png, Clipboard_2021-04-12-08-49-54.png, Clipboard_2021-04-12-08-52-10.png, Clipboard_2021-04-12-08-52-10.png, Clipboard_2021-04-12-22-07-12.png, Clipboard_2021-04-13-09-45-23.png, Clipboard_2021-04-13-09-45-32.png]
tags: [string]
title: Implement strStr()
created: '2021-04-12T12:46:12.015Z'
modified: '2021-04-13T14:30:56.281Z'
---

## Implement strStr()
:dragon_face: **·** `String` **·** `Medium`

Return the index of the first occurrence of needle in haystack, or -1 if needle is not part of haystack. Return 0 if needle is an empty string.`

#### Solution 1: Brute Force
```python
if not needle:
    return 0

for i in range(len(haystack) - len(needle) + 1):
    if haystack[i:i + len(needle)] == needle:
        return i
return -1
```
Time complexity: O(nm), where n is haystack length and m is needle length. There is a faster way to solve this problem in O(n) time using the KMP algorithm.

#### Solution 2: KMP Algorithm
<ul>
<li>First, create the "Longest Proper Prefix which is Suffix" (LPS) array.
    <ul>
      <li>A proper prefix is a prefix of a word that isn't the word itself.</li>
      <li>The LPS array stores the length of a substring that is equal to the prefix.
    </ul>
</li>
</ul>

> For example, the word `ACA` has the following proper prefixes: ` `, `A`, `AC`, and the suffixes: ` `, `A`, `CA`, `ACA`. Thus, the longest proper prefix that is equal to the suffix is `A`. The LPS array is `[0, 0, 1]`.

![](@attachment/Clipboard_2021-04-12-08-52-10.png)

#### Intuition:
* At index 2, `A` is equal to `A` at index 0, so the value of LPS at index 2 = 1. 
* At index 3, `B` is **not** equal to `C` at index 1, so the value of LPS at index 3 = 0. 

![](@attachment/Clipboard_2021-04-12-08-49-54.png)
The LPS array has the same length as the pattern string and is initialized with all zeroes.
Creating the LPS array requires 2 pointers. 
* The bottom pointer iterates over the pattern string. 
* The top pointer is used to determine the LPS of the current substring. 

#### Phase 1:
The bottom pointer moves trying to find a letter that is equal to the first letter of the string, where the top pointer is resting. Once found, we can write 1 in the LPS array at the position of the bottom pointer. 

#### Phase 2:
We move both pointers while they are pointing to equal symbols. We write `top_pointer += 1` (aka the length of the LPS) to the LPS array at the position of the bottom pointer. Eventually, the pointers may be pointing to different symbols, in which case we move on to Phase 3. 

> “We are in the endgame now.”

#### Phase 3:
In “Phase 3” we roll back the top pointer to find the new LPS (which is smaller than the LPS at the previous bottom index). This continues until the top pointer points to a symbol that matches the bottom pointer (we go back to Phase 2), or the top pointer reaches 0 (we go back to phase 1). The program stops once the bottom pointer iterates over the entire string. 

#### The LPS algorithm: implementation
“Phases” are implemented in a reverse order here for readability.
```python
def compute_lps(pattern: str) -> List[int]:
    # Longest Proper Prefix that is suffix array
    lps = [0] * len(pattern)

    top = 0 
    for bottom in range(1, len(pattern)):
        
        # Phase 3: roll the prefix pointer back until match or 
        # beginning of pattern is reached
        while top and pattern[bottom] != pattern[top]:
            top = lps[top - 1]

        # Phase 2: if match, record the LSP at the current bottom pointer
        # and move top pointer
        if pattern[top] == pattern[bottom]:
            top += 1
            lps[bottom] = top

        # Phase 1: is implicit. No match, for loop keeps chugging along

    return lps

```
#### The KMP Pattern Search
![](@attachment/Clipboard_2021-04-12-22-07-12.png)
If a mismatch occurs the algorithm goes to the Phase 3. That is the only phase different from the naive approach. In the naive pattern search when a mismatch is found, the target pointer moves one symbol forward from the place it started the comparison, and the pattern pointer (index) is reset to 0. On contrary, when running KMP, the target pointer remains at the same place, but the pattern pointer is rolled back using the information from the LPS array.

![](@attachment/Clipboard_2021-04-13-09-45-23.png)
> An example of the mismatch found during the patter search. The red dashed line indicates the part of a pattern and a target string matched so far. The green shading represents the Longest prefix, which is the suffix for the current pattern sub-string

The LPS array for the current pattern sub-string tells us that the prefix of length 3 is equal to the suffix (both are shaded in green). This means we can safely move the pattern pointer back to the 4th symbol, because the first 3 letters are already guaranteed to be a match. We leave the target pointer in the same place.

![](@attachment/Clipboard_2021-04-13-09-45-32.png)

This roll back of the pattern pointer repeats until a symbol at the new pattern pointer position matches one at the target pointer (transition to the Phase 2), or the pattern pointer is 0 (transition to the Phase 1).

#### KMP: Implementation
```python
def kmp(needle: str, haystack: str) -> List[int]:
    
    match_indices = [] 
    needle_lps = compute_lps(needle)
    needle_index = 0

    for index, letter in enumerate(haystack):
        
        # Phase 3: if a mismatch was found, roll back the needle
        # index using the information in LPS
        while needle_index and needle[needle_index] != letter:
            needle_index = needle_lps[needle_index - 1]

        # Phase 2: if match
        if needle[needle_index] == letter:
            # If the end of a needle is reached, record the result
            # and use info in LPS array to shift the index
            if needle_index == len(needle) - 1:
                match_indices.append(index - needle_index)
                needle_index = needle_lps[needle_index]
            
            else:
                # Move the needle index forward
                needle_index += 1

        # Phase 1: no match, for loop keeps chugging along 

    return match_indices
```
If only the first occurence of a needle is required, then replace `match_indices.append(index - needle_index)` with `return index - needle_index`


