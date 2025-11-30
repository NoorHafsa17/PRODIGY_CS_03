🚀 NextGen Password Complexity Checker
AI-Driven | Word-Pattern Detection | Attack-Simulation | Realistic Time-to-Crack | Smart Fix Suggestions

This project is Task-03 for PRODIGY CYBERSECURITY Internship, but implemented like a real security engineer would build a production-grade password auditor.

Unlike normal password checkers that only check length and symbols, this tool performs:

✔ Human-word detection (unknown invented words, CamelCase, multi-word passphrases)
✔ PCFG-aware guess modeling
✔ Dictionary, pattern, keyboard, date-pattern detection
✔ Shannon entropy + hybrid attacker model
✔ Simulated brute-force, pattern-based and word-based cracking models
✔ Time-to-crack estimation based on real attacker speeds
✔ Smart password suggestions that are validated for strength
✔ Secure passphrase generator (diceware-style + high entropy mutations)

This tool is built using FastAPI (backend) + HTML/CSS/JS (frontend).

⭐ Features
🔍 Advanced Password Analysis

Detects:

Word-like passwords (even if they are NOT in dictionary)

CamelCase human names or invented words

Multi-word passphrases (OrbitSilentRocket)

Pronounceable human-like strings

Keyboard patterns (qwerty, asdf)

Leet speak: p@ssw0rd → flagged

Repetitive sequences

Date-like patterns (1999, 2022)

🔐 Hybrid Strength Scoring

Uses:

Shannon entropy

Character category variety

Word-based guessing model

Pattern-based model

Penalty for human-readable structures

Conservative caps to avoid misleading "Strong" labels

⚡ Time-to-Crack Estimation

Based on 10M guesses/sec attacker speed, supporting:

brute force

hybrid dictionary

word-mutation attacks

🧠 Smart Suggestion Generator

Produces only high-entropy, non-word-like, validated strong passwords.

Includes:

random high-entropy variants

diceware-hybrid generator

mutated rare-word generator

strength-checked replacements

Suggestions are validated to meet a minimum cracking threshold (≥ 10¹² guesses).

🛠 Built With

FastAPI (backend API)

JavaScript frontend

HTML5 + CSS3

Uvicorn (server)


⚙️ How to Run Locally
1️⃣ Install dependencies
pip install fastapi uvicorn

2️⃣ Start Backend
uvicorn server:app --reload


Server runs at:
👉 http://127.0.0.1:8000

3️⃣ Start Frontend

From the web/ folder:

python -m http.server 8080


Open in browser:
👉 http://127.0.0.1:8080

🧪 API Usage
POST /check

Analyze password strength.

Request

{
  "password": "Hello@123",
  "leaked": false
}


Response

{
  "score": 45,
  "label": "Fair",
  "reasons": ["low entropy"],
  "entropy_bits": 22.3,
  "guesses_estimate": 43000000,
  "ttc": "4.9 hours",
  "suggestions": [
     {
       "example": "Luna!X4$92@qW...",
       "score": 95,
       "label": "Strong",
       "ttc": "115.7 days",
       "why": "auto-generated strong password",
       "cost": "replace"
     }
  ]
}

🛡 Why This Checker Is Superior (Compared to Normal Tools)

Normal checkers fail because they:

Mark OrbitSilentRocket! as Strong (WRONG)

Mark Hello11@123# as Strong (WRONG)

Think invented words are unguessable (WRONG)

Use only entropy → attacker doesn’t care about entropy (WRONG)

This tool:
✔ detects invented words
✔ blocks all readable word patterns
✔ uses conservative attacker modeling
✔ shows realistic time-to-crack
✔ ensures suggestions are truly strong

🎯 Use Cases

User password auditing

Security awareness tools

Enterprise password policy enforcement

College cybersecurity projects

Internship task submission

Recruiter portfolio project

GitHub project to showcase real cybersecurity engineering skills

🏁 Conclusion

This project is not just a “Task-03” submission —
it is a weapon-grade password evaluation engine built like a real infosec engineer.

It demonstrates:

attacker mindset

secure coding

API development

UI/UX

randomness handling

modern cybersecurity design
