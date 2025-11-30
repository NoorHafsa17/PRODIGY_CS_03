NextGen Password Strength & Attack-Model Analyzer
<p> <img src="https://img.shields.io/badge/Category-Cybersecurity-blueviolet"> <img src="https://img.shields.io/badge/Backend-FastAPI-009688"> <img src="https://img.shields.io/badge/Frontend-HTML%2FJS-blue"> <img src="https://img.shields.io/badge/Security-Attacker--Model-critical"> <img src="https://img.shields.io/badge/Password%20Cracking-PCFG%20%7C%20Entropy-green"> </p>

A password-strength engine built using real attacker modeling, not naive entropy checks.
It identifies word structures, CamelCase, multi-word passphrases, pronounceable patterns,
keyboard sequences, and PCFG-style guess patterns — even for invented words.

1. Overview

Traditional password checkers give false results because they rely only on length or entropy.
This tool analyses passwords the way attackers actually do:

Human-word structure detection

CamelCase / multi-word splitting

Dictionary + mutation modeling

Entropy + character diversity scoring

Keyboard patterns

Date patterns

PCFG-like structure scoring

Realistic time-to-crack (10M guesses/sec)

It produces accurate strength, realistic crack times, and validated strong suggestions.

2. Features
Word & Pattern Detection

Detects invented words (e.g., OrbitSilentRocket)

Flags CamelCase

Detects readable multi-word strings

Finds pronounceable vowel–consonant patterns

Detects keyboard sequences (qwerty, asdf)

Identifies repetition / date-like segments

Attack-Model Scoring

Shannon entropy

Word-rank based guess modeling

Mutation / hybrid attack logic

Pattern-based cracking heuristics

Conservative caps for human-readable forms

Validated Strong Suggestions

High-entropy random strings

Diceware-hybrid passphrases

Rare-word + mutation patterns

Suggestions validated to ≥ 10¹² guesses

All outputs checked to avoid word-like structures

3. Tech Stack
Component	Technology
Backend	FastAPI, Uvicorn
Frontend	HTML, CSS, JavaScript
Security RNG	Python secrets
Modeling Approach	Entropy + Word-pattern + PCFG-style
4. Project Structure
PRODIGY_CY_03/
├── server.py
├── web/
│   ├── index.html
│   ├── style.css
│   └── script.js
└── README.md

5. Running the Project
Backend
pip install fastapi uvicorn
uvicorn server:app --reload


Server → http://127.0.0.1:8000

Frontend
cd web
python -m http.server 8080


Frontend → http://127.0.0.1:8080

6. API Usage
POST /check
Request
{
  "password": "Hello@123",
  "leaked": false
}

Response
{
  "score": 42,
  "label": "Fair",
  "entropy_bits": 21.9,
  "guesses_estimate": 43000000,
  "ttc": "4.9 hours",
  "reasons": ["low entropy"],
  "suggestions": [...]
}

7. Why This Tool Is Different
Capability	Typical Checkers	This Tool
Detect invented/human words	✖	✔
Detect CamelCase	✖	✔
Pronounceability detection	✖	✔
PCFG-style modeling	✖	✔
Realistic crack-time	✖	✔
Validated strong suggestions	✖	✔

Uses attacker strategy modeling, not superficial entropy-based scoring.

8. Use Cases

Cybersecurity awareness

Password audits

Pen-testing tools

Enterprise password validation

Developer security reviews

College / internship projects

Research demonstrations

9. Final Notes

This project applies an offensive-security mindset, evaluating passwords through
structure, patterns, entropy, and attacker behavior, not simple rules.
