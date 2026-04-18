# Hangman Game

A Python implementation of the classic Hangman word-guessing game with hint functionality.

## Overview

This project implements the Hangman game, where players guess letters to figure out a secret word. The game includes two modes:
1. **Standard Hangman** - Basic guessing with warnings
2. **Hangman with Hints** - Includes a hint system to show possible word matches

## Features

- **Warning System**: Players start with 3 warnings for invalid inputs or duplicate guesses
- **Guesses Tracking**: Players start with 6 guesses to find the secret word
- **Vowel Penalty**: Incorrect guesses on vowels cost 2 guesses, consonants cost 1
- **Hint System**: Type `*` to see all possible words matching your current guess
- **Score Calculation**: Final score = remaining guesses × number of unique letters in the word

## Files

- `hangman.py` - Main game implementation
- `words.txt` - Dictionary of valid English words used for gameplay

## How to Play

### Running the Game

```bash
python hangman.py
```

### Game Rules

1. The computer selects a random word from the word list
2. You have **6 guesses** and **3 warnings** to start
3. Each round, guess one letter at a time
4. For **invalid inputs** or **duplicate guesses**:
   - First 3 times: Lose a warning
   - After warnings expire: Lose a guess
5. **Wrong guesses on vowels** cost 2 guesses
6. **Wrong guesses on consonants** cost 1 guess
7. Win by revealing all letters before running out of guesses

### Using Hints

Type `*` when prompted for a guess to see all possible words that match your current game state.

## Functions

### Core Game Functions

| Function | Purpose |
|----------|---------|
| `load_words()` | Loads the word list from words.txt |
| `choose_word(wordlist)` | Selects a random word from the list |
| `is_word_guessed(secret_word, letters_guessed)` | Checks if the word is completely guessed |
| `get_guessed_word(secret_word, letters_guessed)` | Returns the current game state (letters and underscores) |
| `get_available_letters(letters_guessed)` | Returns remaining available letters to guess |

### Game Modes

| Function | Description |
|----------|-------------|
| `hangman(secret_word)` | Starts a standard Hangman game |
| `hangman_with_hints(secret_word)` | Starts Hangman with hint functionality |

### Hint System Functions

| Function | Purpose |
|----------|---------|
| `match_with_gaps(my_word, other_word)` | Checks if a word matches the current game state |
| `show_possible_matches(my_word)` | Displays all valid words matching the current guess |

## Example Gameplay

```
Welcome to the game Hangman!
I am thinking of a word that is 6 letters long.
You have 3 warnings left.
-----------
You have 6 guesses left.
Available letters: abcdefghijklmnopqrstuvwxyz
Please guess a letter: e
Good guess: _ _ _ _ _ e

You have 6 guesses left.
Available letters: abcdfghijklmnopqrstuvwxyz
Please guess a letter: a
Oops! That letter is not in my word: _ _ _ _ _ e

You have 4 guesses left.
```

## Requirements

- Python 3.x
- `words.txt` file in the same directory

## Error Handling

The game validates user input and handles:
- Non-alphabetic characters
- Duplicate guesses
- Invalid inputs (with warning system)

## Scoring

Your final score is calculated as:

$$\text{Score} = \text{Remaining Guesses} \times \text{Number of Unique Letters in Word}$$

Example: If you win with 4 guesses remaining and the word has 5 unique letters: `4 × 5 = 20 points`

## Notes

- All words in the dictionary are lowercase
- The game is case-insensitive (both uppercase and lowercase inputs work)
- The hint function (`*`) is only available in the `hangman_with_hints()` mode
