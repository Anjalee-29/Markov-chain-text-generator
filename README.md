# Markov-chain-text-generator

A lightweight Flask web application that generates text using a **Markov Chain** algorithm — no ML models, no GPU required. Paste in any sample text, choose an output length, and the app learns word transitions on the fly to generate new text in a similar style.

---

## Features

- **Markov Chain text generation** — pure Python, built with `random` and `collections.defaultdict`; no external ML libraries needed
- **Custom input** — paste any text as the training corpus per request
- **Adjustable output length** — choose how many words to generate (1–100)
- **Two-page Flask UI** — clean input form and a separate results page with a "Generate Another" link
- **No model downloads** — runs instantly, works offline

---

## How It Works

1. Your input text is split into words
2. A Markov chain is built mapping each word to all words that follow it in the text
3. Generation starts from a random word and walks the chain, picking the next word randomly from observed successors
4. The result is a sequence of `length` words that statistically mirrors your input

---

## Project Structure

```
.
├── app.py              # Flask app — Markov chain logic and routes
├── index.html          # Input form (move to templates/ before running)
├── result.html         # Results page (move to templates/ before running)
├── style.css           # Stylesheet (move to static/ before running)
└── README.md
```

> **Before running**, reorganise the files like this:
> ```
> ├── app.py
> ├── templates/
> │   ├── index.html
> │   └── result.html
> ├── static/
> │   └── style.css
> └── README.md
> ```

---

## Requirements

- Python 3.8+
- Flask

Install dependencies:

```bash
pip install flask
```

That's it — no PyTorch, no Transformers, no model downloads.

---

## Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/markov-chain-text-generator.git
   cd markov-chain-text-generator
   ```

2. **Reorganise files**
   ```bash
   mkdir templates static
   mv index.html result.html templates/
   mv style.css static/
   ```

3. **Run the app**
   ```bash
   python app.py
   ```

4. Open your browser at `http://127.0.0.1:5000`

---

## Usage

1. Paste any text into the **sample text** box (the more text, the better the output)
2. Enter the desired **output length** in words (default: 10, max: 100)
3. Click **Generate Text**
4. View the generated output — click **Generate Another** to go back and try again

**Tip:** Longer and more varied input text produces more interesting results. Try pasting a news article, a book excerpt, or song lyrics.

---

## Routes

| Route | Method | Description |
|---|---|---|
| `/` | GET | Input form |
| `/generate` | POST | Builds the chain and returns generated text |
