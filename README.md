---
# Senegalese License Plate Detection Program

---

This program detects Senegalese vehicle license plates in any text string, supporting multiple formats and handling split words, spaces, or hyphens. Below is a step-by-step explanation of the solution.

## Objective
The goal was to **detect valid license plates** embedded in a text, specifically in the formats:  

- `XY-1234-T`  
- `XY 1234 T`  
- `XY-1234-ZT`  
- `xy 1234 zt`  

A key requirement was that **plates must be separated from other words** by spaces or punctuation — plates “stuck” to other words should **not** be detected.

---

## Approach
1- `is_plate(candidate)`
This function verifies whether a given string (usually of length 10) matches the Senegalese plate format.

**Logic:**
- Checks positions of letters, digits, and separators (- or space).
- Uses a manual digit = "0123456789" definition for strict validation.
- Determines if the plate is of type XY-1234-T (9 chars) or XY-1234-ZT (10 chars).
- Returns (True, normalized_plate) if valid, or False otherwise.

2- `normalize(candidate)`
This function ensures all plates follow the same standardized format using dashes.
**Logic:**
- Replaces spaces at fixed positions (2 or 7) with -.
- Returns the cleaned plate in the canonical form:
→ e.g., "DK 1234 T" → "DK-1234-T".

3- `detection(text)`
This function scans the entire text to extract valid, normalized plates.

**Logic:**
- Iterates character by character.
- For each alphabetic character, takes the next 9 characters as a possible plate.
- Uses is_plate() for validation and normalize() for formatting.
- Ensures the plate is not attached to a word on either side.
- Returns a list of all valid and normalized detected plates in the text.

4- `main()`

A minimal interactive interface for user testing.

**Behavior:**
- Prompts the user to enter text repeatedly.
- Displays the count and list of detected plates.
- Quits gracefully when the user types q.

---
## Summary :
| Function      | Purpose                         | Key Role                                     |
| ------------- | ------------------------------- | -------------------------------------------- |
| `is_plate()`  | Validate plate structure        | Confirms the pattern matches official format |
| `normalize()` | Standardize spacing and hyphens | Ensures visual consistency                   |
| `detection()` | Extract plates from text        | Finds valid, isolated plates                 |
| `main()`      | Interactive testing             | Allows manual verification                   |

---
## Outcome

The final system is:

**Pure Python**

**Case-insensitive**

**Strict and efficient**
