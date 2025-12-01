# DELTA-K Cipher Encoder
A simple, lightweight CLI tool for encrypting plaintext messages into ciphertext via the DELTA-K cipher.

## What is DELTA-K?
The DELTA-K Cipher Encoder program is, as the title suggests, based on the DELTA-K cipher. The DELTA-K cipher is a substitution cipher I created, fundamentally built on the trinary (Base-3) number system.

The cipher utilizes three glyphs, ▲, ▼, and ◆, which correspond to numbers 0, 1, and 2 respectively. Every letter in the alphabet is mapped to a triplet of glyphs correspondent to that letter's trinary position in the alphabet. The following table lists all the standard alphabetical mappings:
| Latin Letter | Alphabetical Position (Trinary) | Associated Glyphs |
|---|---|---|
| A | 001 | ▲▲▼ |
| B | 002 | ▲▲◆ |
| C | 010 | ▲▼▲ |
| D | 011 | ▲▼▼ |
| E | 012 | ▲▼◆ |
| F | 020 | ▲◆▲ |
| G | 021 | ▲◆▼ |
| H | 022 | ▲◆◆ |
| I | 100 | ▼▲▲ |
| J | 101 | ▼▲▼ |
| K | 102 | ▼▲◆ |
| L | 110 | ▼▼▲ |
| M | 111 | ▼▼▼ |
| N | 112 | ▼▼◆ |
| O | 120 | ▼◆▲ |
| P | 121 | ▼◆▼ |
| Q | 122 | ▼◆◆ |
| R | 200 | ◆▲▲ |
| S | 201 | ◆▲▼ |
| T | 202 | ◆▲◆ |
| U | 210 | ◆▼▲ |
| V | 211 | ◆▼▼ |
| W | 212 | ◆▼◆ |
| X | 220 | ◆◆▲ |
| Y | 221 | ◆◆▼ |
| Z | 222 | ◆◆◆ |

The encryption process is simply mapping each letter to the corresponding glyph triplet. For example, the plaintext "HELLO WORLD" is encrypted into "▲◆◆▲▼◆▼▼▲▼▼▲▼◆▲/◆▼◆▼◆▲◆▲▲▼▼▲▲▼▼" (forward slashes representing spaces).

When encrypted as-is, the DELTA-K cipher is a fairly simple monoalphabetic substitution cipher. This is the DELTA-K cipher's "**Standard Mode**." However, DELTA-K also supports another mode, which is where the real fun comes in: "**Delta Mode**."

Delta Mode transforms DELTA-K from a simple monoalphabetic substitution cipher into a significantly more complicated polyalphabetic substitution cipher, with functionality similar to the Vigenère cipher. Here's how it works:

1. Pick a keyword (must be alphabetical with no spaces) and line it up with your plaintext. In the given example, the keyword is "KEY", and the plaintext is "HELLO WORLD".

> HELLO WORLD
>
> KEYKE YKEYK
   
3. Convert the plaintext and the key to their corresponding trinary values.

> 022 012 110 110 120 | 212 120 200 110 011
> 
> 102 012 221 102 012 | 221 102 012 221 102

3. Add the numbers in each column together.

> 124 024 331 212 132 | 433 222 212 331 113

4. Perform modulo-3 division on each digit.

> 121 021 001 212 102 | 100 222 212 001 110

5. Convert the numbers to their corresponding glyphs.

> ▼◆▼▲◆▼▲▲▼◆▼◆▼▲◆/▼▲▲◆◆◆◆▼◆▲▲▼▼▼▲

This produces a completely different result than doing it normally, one that is significantly more difficult to decode without knowing what the key itself is. Attempting to decode the previous example's ciphertext normally would give "PGAWK IZWAL", which is obviously very different from the actual plaintext, and cannot be decrypted using simple frequency analysis.

## Features
- Inventive Encryption: Being that this cipher is entirely custom-made, you are unlikely to find it anywhere else.
- Ease-of-Use: As a lightweight CLI tool, this program is designed to be fast and easy to use.
- Modularity: You can encrypt plaintext in either Standard Mode (unkeyed, monoalphabetic) or Delta Mode (keyed, alphabetic).
- Zero Dependencies: Requires no outside libraries. All logic is handled via the Standard Library and helper functions.

## Installation & Usage
Lorem ipsum

## Roadmap
Right now, this project is very barebones. It is functional, but still only a rudimentary single-execution CLI program. Below is a roadmap outlining what is done, and what I'd like to implement in the future.
- [x] Implement basic encryption logic
- [x] Add Delta Mode (keying) encryption functionality
- [ ] Implement basic decryption logic
- [ ] Add Delta Mode decryption functionality
- [ ] Allow for encryption/decryption of whole .txt files
- [ ] Build interactive UI beyond CLI
- [ ] Implement more advanced double-keyed encryption/decryption?

Contributions towards these goals are welcome!

## License
Lorem ipsum

## Attribution
Coding: Kazy (agender-nerd)

Comments: Gemini AI
