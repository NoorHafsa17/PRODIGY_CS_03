NextGen Password Strength & Attack-Model Analyzer
<p> <img src="https://img.shields.io/badge/Category-Cybersecurity-blueviolet"> <img src="https://img.shields.io/badge/Backend-FastAPI-009688"> <img src="https://img.shields.io/badge/Frontend-HTML%2FJS-blue"> <img src="https://img.shields.io/badge/Security-Attacker--Model-critical"> <img src="https://img.shields.io/badge/Password%20Cracking-PCFG%20%7C%20Entropy-green"> </p>

A password-strength engine that uses attacker-realistic models instead of only entropy or character checks.
It detects human-word structures, CamelCase, multi-word passphrases, keyboard patterns, pronounceable strings, and PCFG-style patterns—even for invented words like OrbitSilentRocket.

Built with FastAPI, Python, and secure randomness using secrets.

1. Overview

Most password checkers give misleading results.
This tool evaluates passwords using:

Word-like structure detection

PCFG pattern modeling

Dictionary + mutation attack simulation

Shannon entropy

Keyboard and date-pattern detection

Realistic crack-time estimation (based on 10M guesses/sec)

Validated strong password suggestions

This reflects how real attackers guess passwords.

2. Key Features
Human-Word Detection

Detects invented human-readable words

Flags multi-word passphrases

Flags CamelCase compositions

Detects pronounceable vowel-consonant patterns

Attack-Model Scoring

Word-based ranking

Pattern-based cracking

Keyboard sequence detection

Repeated-character detection

Hybrid entropy + attacker modeling

Smart Suggestions

High-entropy random passwords

Diceware-hybrid passphrases

All suggestions validated to meet ≥ 10¹² guess threshold

Ensures suggestions are not word-like or predictable

3. Tech Stack
Layer	Technology
Backend	FastAPI, Uvicorn
Frontend	HTML, CSS, JavaScript
Security RNG	Python secrets
Strength Model	Entropy + PCFG-like + Pattern Detection
4. Project Structure
PRODIGY_CY_03/
│── server.py            # Backend (FastAPI) - password analysis engine
│── web/
│     ├── index.html     # Frontend UI
│     ├── style.css      # UI styling
│     └── script.js      # API communication + UI logic
└── README.md

5. How to Run
Backend
pip install fastapi uvicorn
uvicorn server:app --reload


Backend available at:
http://127.0.0.1:8000

Frontend
cd web
python -m http.server 8080


Open in browser:
http://127.0.0.1:8080

6. API Usage
POST /check

Request

{
  "password": "Hello@123",
  "leaked": false
}


Response (example)

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
Capability	Normal Checkers	This Tool
Detect invented words	✖	✔
Detect CamelCase	✖	✔
Detect pronounceable patterns	✖	✔
Pattern-based attacker model	✖	✔
Realistic crack-time	✖	✔
Validated strong suggestions	✖	✔

This tool treats passwords the way attackers do—through structure, patterns, and guessability.

8. Use Cases

Cybersecurity audits

Pen-testing tools

Password policy validation

Developer security checks

Awareness programs

College projects

Internship submissions

Security research demos

9. Final Notes

This project is built with an offensive-security mindset, combining entropy, human-pattern detection, and hybrid attack simulation for accurate password evaluation.
