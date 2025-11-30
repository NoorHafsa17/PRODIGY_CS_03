NextGen Password Strength & Attack-Model Analyzer
<p> <img src="https://img.shields.io/badge/Category-Cybersecurity-blueviolet"> <img src="https://img.shields.io/badge/Backend-FastAPI-009688"> <img src="https://img.shields.io/badge/Frontend-HTML%2FJS-blue"> <img src="https://img.shields.io/badge/Security-Attacker--Model-critical"> <img src="https://img.shields.io/badge/Password%20Cracking-PCFG%20%7C%20Entropy-green"> </p>

A password-strength engine built using real attacker models, not superficial checks.
Analyzes word patterns, CamelCase, multi-word passphrases, keyboard sequences,
vowel–consonant human-readable patterns, and PCFG-style guess modeling.

Designed for realistic password auditing.

1. Overview

Typical password checkers only measure entropy or length.
This tool performs attacker-style analysis, including:

Word-like structure detection

Multi-word/CamelCase detection

Dictionary + mutation modeling

Shannon entropy estimation

Keyboard sequence detection

Pattern-based attack guessing

Time-to-crack simulation (10M guesses/sec)

Strong suggestion generation with validation

2. Features
Word & Pattern Detection

Detects invented human-like words

Flags multi-word passphrases

Finds CamelCase segments

Detects pronounceable vowel/consonant patterns

Identifies keyboard sequences (qwerty, asdf)

Detects dates and repeated sequences

Hybrid Strength Scoring

Entropy-based calculation

PCFG-inspired cracking heuristics

Word-ranking based guess simulation

Penalties for human-readable structures

Realistic guess caps to avoid misleading scores

Strong Suggestion Generator

High-entropy random passwords

Diceware-hybrid passphrases

Rare-word + mutation combinations

All suggestions validated against the attacker model

3. Tech Stack
Component	Technology
Backend	FastAPI + Uvicorn
Frontend	HTML, CSS, JavaScript
Security RNG	Python secrets
Modeling Approach	Entropy + Word-pattern + PCFG-style
4. Project Structure
PRODIGY_CY_03/
│── server.py
│── web/
│     ├── index.html
│     ├── style.css
│     └── script.js
└── README.md

5. Installation & Running
Backend
pip install fastapi uvicorn
uvicorn server:app --reload


Backend: http://127.0.0.1:8000

Frontend
cd web
python -m http.server 8080


Frontend: http://127.0.0.1:8080

6. API Usage
POST /check

Request:

{
  "password": "Hello@123",
  "leaked": false
}


Response (example):

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
Feature	Typical Checkers	This Tool
Detect invented words	✖	✔
Detect CamelCase	✖	✔
Pronounceability detection	✖	✔
PCFG-like modeling	✖	✔
Realistic time-to-crack	✖	✔
Validated suggestions	✖	✔

This project applies real attacker logic, not superficial checks.

8. Use Cases

Cybersecurity awareness

Password policy testing

Pen-testing utilities

Enterprise auditing

College cybersecurity projects

Developer security review

Internship/portfolio project

9. Final Notes

This engine combines entropy metrics, human-pattern detection,
and hybrid attack modeling to give realistic password evaluations.
