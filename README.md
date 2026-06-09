# Trusted AI Pathway — Self-Assessment

Interactive, single-file web pages that let a customer find **where they sit on the Trusted AI Pathway** by scoring how AI is used in their organisation today. Built for the **Microsoft Innovation Hub Brussels**.

The pathway has four stages — **Discover → Ready → Govern → Scale** — and the assessment places the respondent on the stage their reality most strongly resembles.

| Stage | Signature question | Value driver |
|------|--------------------|--------------|
| 1 — Discover | *Where does this help me?* | Individual productivity |
| 2 — Ready | *What happens to our data when everyone starts using it?* | Data confidence |
| 3 — Govern | *What is AI doing in our organisation?* | Agents under control |
| 4 — Scale | *How do we deploy AI agents safely and consistently across the enterprise?* | Enterprise operations |

---

## The two questionnaires

There is one page per audience, because the people answering see very different things:

| Page | Audience | Statements | Focus |
|------|----------|-----------|-------|
| `Trusted_AI_Pathway_Assessment_End_User.html` | End users | 27 | How the tool is actually used day to day — habits, team usage, agents acting on their behalf. No IT/Security knowledge needed. |
| `Trusted_AI_Pathway_Assessment_IT_Security.html` | IT / Security admins | 10 | Posture, visibility, governance, identity & access — answerable from the admin perspective. |

Each statement is drawn from the corresponding stage's **characteristics** and **voices** in the Trusted AI Pathway deck.

> Companion Excel versions (`.xlsx`) of each questionnaire are included for a saved, fillable record. They use the same statements, scoring, and placement logic.

---

## How it works

1. Open the `.html` file in any modern browser (no install, no internet required).
2. Each statement has a **1–5 slider** — *1 = not true at all, 5 = completely true* of your organisation today.
3. Statements are **deliberately mixed across stages** (not grouped), so respondents answer blind and don't steer toward a result.
4. The side panel updates live, showing:
   - your **strongest-matching stage**, its value driver, signature question, and recommended Innovation Hub engagement;
   - a **profile bar** for all four stages so transitions are visible.

### Scoring & placement

- Every statement is tagged (internally) to one of the four stages.
- Each stage's score is the **average** of its statements' slider values; **match % = average ÷ 5**.
- Your **current stage = the stage with the highest average** (the one your reality most resembles).
- A high later-stage score with lower earlier stages indicates you are **transitioning into** that stage.

---

## Buttons

- **Email report** — opens your default mail client with the results pre-filled (recipient, subject, outcome, stage profile, and every scored answer). *Note: a static page cannot send mail itself; it hands a `mailto:` message to your mail client to send.*
- **Print / PDF** — produces a **printer-friendly** layout: the **assessment outcome prints first**, then a page break, then the answers on a new page (sliders are replaced with a clean `Score: N` line).
- **Reset** — returns all sliders to 1.

---

## Privacy

The pages are **fully client-side**. All scoring happens in the browser; **no data is sent anywhere**. The only outbound action is the optional **Email report** button, which simply opens your own mail client with a draft — nothing is transmitted automatically.

---

## Hosting

Because each page is a **single self-contained HTML file** with inline CSS/JS and no external dependencies, you can:

- double-click to open locally, or
- serve it from any static host (e.g. **GitHub Pages**): commit the file and enable Pages, then share the URL.

---

## Customising

The pages are generated from **`generate_assessment.py`** (Python + `openpyxl`). To change statements, stages, colours, or the recipient of the Email button:

1. Edit the `END_USER_ITEMS` / `ADMIN_ITEMS` lists, `STAGE_META`, or the `TEMPLATE` string.
2. Regenerate:
   ```bash
   python generate_assessment.py
   ```
   This rebuilds both `.html` and both `.xlsx` files into `output/`.

Each item is a tuple `(stage, kind, text)` where `stage` is `1–4`, `kind` is `"Characteristic"` or `"Voice"`, and `text` is the statement shown to the respondent. Statement order is shuffled with a fixed seed so the Excel and HTML versions stay in sync.

---

## Files

```
Trusted_AI_Pathway_Assessment_End_User.html      # end-user questionnaire (web)
Trusted_AI_Pathway_Assessment_End_User.xlsx       # end-user questionnaire (Excel)
Trusted_AI_Pathway_Assessment_IT_Security.html    # IT/Security questionnaire (web)
Trusted_AI_Pathway_Assessment_IT_Security.xlsx    # IT/Security questionnaire (Excel)
generate_assessment.py                            # generator for all of the above
README.md
```

---

## Credits

Trusted AI Pathway — Microsoft Innovation Hub Brussels.
Owner: **Bart Gabriëls**, Sr. Solution Engineer, Trust & AI.
