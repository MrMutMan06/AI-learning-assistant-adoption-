# Data dictionary

**Source:** Global ChatGPT Student Survey (Ravšelj, Aristovnik et al.), CC BY 4.0. Two waves:

| Wave | File | Shape (rows × columns) |
|---|---|---|
| 2023–24 | `data/raw(2023-2024).csv` | 23,218 × 174 |
| 2024–25 | `data/raw(2024-2025).csv` | 22,963 × 180 |

Every column is named after its question number in the questionnaires (`data/questionnaire(2023-2024).pdf`, `data/questionnaire(2024-2025).pdf`). Almost every answer is stored as a **number code**. This dictionary covers the columns our research questions use and translates their codes back into meaning.

## How to read this dictionary

- **Type** gives both the Pandas dtype (what `df.dtypes` reports) and the *kind* of variable it really is. Most columns are `float64` only because a column of integer codes that contains `NaN` cannot be stored as `int64`. The codes are ranked categories, not quantities: "Agree" (4) is not twice "Disagree" (2).
- **Observed missing** is `df[col].isna().mean()` in the raw files, shown as 2023–24 / 2024–25.
- **Expected missing values** explains *why* a blank is normal for that column. The survey has skip logic (see the note at the end), so many blanks are by design rather than errors.

## Shared answer scales

Most columns use one of these two five-point scales.

| Code | Agreement scale (A) | Frequency scale (F) |
|---|---|---|
| 1 | Strongly disagree | Never |
| 2 | Disagree | Rarely |
| 3 | Neutral | Sometimes |
| 4 | Agree | Often |
| 5 | Strongly agree | Always |

## Columns

| Column | Type | Meaning (questionnaire wording) | Units / categories | Observed missing | Expected missing values |
|---|---|---|---|---|---|
| `Q1` | `str`; nominal | What is your citizenship? | Country name as text (149 / 155 distinct values) | 6.4% / 7.5% | Low. Item non-response only (the drop-down could be skipped). |
| `Q3` | `float64` (2023–24), `str` (2024–25); numeric | How old are you (in years)? | Years; questionnaire range 18–100 | 0.9% / 1.3% | Low. Contains invalid entries, left unchanged: 87 values outside 18–100 in 2023–24 (e.g. 2, 333, birth years such as 2000), and 2 in 2024–25. In 2024–25 it reads as text because of two typed entries (`"20Years"` and `"19"` followed by the Arabic word for "year"). |
| `Q4` | `str`; nominal | In which country are you studying during this semester? | Country name as text (109 / 120 distinct values) | 1.3% / 1.8% | Low. Item non-response only. |
| `Q8` | `float64`; ordinal | What level of study are you enrolled in? | 1 = Bachelor's level (1st), 2 = Master's level (2nd), 3 = Doctoral (3rd) | 2.2% / 2.5% | Low. Item non-response only. |
| `Q10` | `float64`; nominal | What is your main field of study? | 1 = Arts and Humanities, 2 = Social Sciences, 3 = Applied Sciences, 4 = Natural and Life Sciences | 2.6% / 3.1% | Low. Item non-response only. |
| `Q13` *(2023–24 only)* | `float64`; binary | Have you ever used ChatGPT? | 1 = Yes, 2 = No | 3.5% / — | Low. Not present in 2024–25 (see `Q13a`–`Q13f`). |
| `Q13a`–`Q13f` *(2024–25 only)* | `float64`; binary (one column per tick box) | Which of the following generative AI chatbots have you used? a = ChatGPT, b = Microsoft Copilot, c = Google Gemini, d = Perplexity AI, e = Claude AI, f = Other (named in `Q13f_text`) | 1 = ticked, 0 = not ticked | — / 5.9% | Low; all six are blank for the same rows. Codes differ from 2023–24 `Q13` (0 means "no" here, 2 means "no" there). `Q13a` is the equivalent of the old `Q13`. |
| `Q14` | `float64`; nominal | Which version of ChatGPT do you use? | 1 = Free, 2 = Subscription, 3 = Both. (2023–24 labels: "ChatGPT-3.5 (free)" and "ChatGPT-4 (subscription)") | 31.4% / 14.7% | **Structural.** Non-users skip to Section 10, so blank for every non-user and for those who left `Q13` blank. |
| `Q15` | `float64`; ordinal | To what extent do you use ChatGPT in general? | 1 = Rarely, 2 = Occasionally, 3 = Moderately, 4 = Considerably, 5 = Extensively | 31.4% / 14.7% | **Structural**, as for `Q14`. Among ChatGPT users, fewer than 110 blanks in each wave. |
| `Q18a`–`Q18l` | `float64`; ordinal | How often do you use ChatGPT for the following tasks? a Academic writing, b Professional writing, c Creative writing, d Proofreading, e Brainstorming, f Translating, g Summarising, h Calculating help, i Study assistance, j Personal assistance, k Research assistance, l Coding assistance | Scale F (1 = Never … 5 = Always) | ≈31.5% / ≈14.8% | **Structural**, as for `Q14`. |
| `Q20` | `float64`; nominal | Does your institution have policies or a code of ethics regarding the use of ChatGPT for students? | 1 = Yes, 2 = No, 3 = I don't know | 37.8% / 21.9% | **Structural + drop-out.** Blank for non-users, and for users who quit before Section 4. Code 3 ("I don't know") is a valid **answer**, not a missing value. |
| `Q22b` | `float64`; ordinal | ChatGPT might encourage students to cheat. | Scale A | 37.6% / 21.7% | **Structural + drop-out**, as for `Q20`. |
| `Q24e` | `float64`; ordinal | I am satisfied with the level of assistance provided by ChatGPT. | Scale A | 40.2% / 24.4% | **Structural + drop-out.** Rises further because Section 5 comes later in the survey. |
| `Q26e` | `float64`; ordinal | ChatGPT can increase my study efficiency. | Scale A | 42.4% / 26.8% | **Structural + drop-out** (Section 6). |
| `Q27b` | `float64`; ordinal | ChatGPT can improve my grades. | Scale A | 42.4% / 26.8% | **Structural + drop-out** (Section 6). |
| `Q32a`–`Q32o` | `float64`; ordinal | How often do you feel the following emotions while using ChatGPT? a Bored, b Hopeful, c Sad, d Ashamed, e Calm, f Angry, g Relieved, h Happy, i Proud, j Anxious, k Surprised, l Curious, m Excited, n Confused, o Frustrated | Scale F (1 = Never … 5 = Always) | ≈46.4% / ≈31.5% | **Structural + drop-out.** The highest missingness of any section we use, because Section 9 is the last one shown only to users. |
| `Q33` | `float64`; ordinal | How would you rate the level of difficulty of your studies? | 1 = Much too easy, 2 = Somewhat easy, 3 = Just about right, 4 = Somewhat challenging, 5 = Extremely challenging | 23.1% / 24.2% | **Drop-out only.** Section 10 is shown to users *and* non-users, so blanks mean the respondent quit before the end. |
| `Q35a` | `float64`; ordinal | I am successful in my studies. | Scale A | 23.0% / 24.1% | **Drop-out only**, as for `Q33`. Answered by non-users too, so it allows a user vs non-user comparison. |

## Note on skip logic: why so many blanks are expected

The questionnaire branches after `Q13`. Respondents who have **not** used ChatGPT skip Sections 2–9 and go straight to Section 10 (study and personal information). Respondents can also stop part-way through, so missingness rises section by section.

| Section | Who sees it | Columns above | Missing because of |
|---|---|---|---|
| 1. Sociodemographics | Everyone | `Q1`–`Q10` | Item non-response only |
| 2–9. Usage → Emotions | ChatGPT users only | `Q14`–`Q32` | Skip logic + drop-out |
| 10. Study and personal | Everyone | `Q33`, `Q35a` | Drop-out only |

So a blank `Q15` for a non-user does **not** mean bad data: the question never applied to them. Any Week 3 treatment of missing values should handle the two kinds differently.

## Differences between the two waves

| Column | 2023–24 | 2024–25 | Consequence when combining the waves |
|---|---|---|---|
| `Q13` | One column, 1 = Yes / 2 = No | Six tick-box columns `Q13a`–`Q13f`, 1 = ticked / 0 = not | Build one shared column (e.g. `uses_chatgpt`) from `Q13` and `Q13a` before concatenating |
| `Q14` | Labels name the models (ChatGPT-3.5 / ChatGPT-4) | "Free version" / "With a subscription" | Same codes and meaning; note in limitations |
| `Q3` | `float64` | `str` (two typed entries) | Convert with `pd.to_numeric(..., errors="coerce")` in Week 3 and log it |

All other columns above share the same names, codes and meaning in both waves.

---
*Prepared with assistance from Claude (Anthropic). Every code, count and percentage was checked against the raw CSVs and both questionnaires; the raw data was not modified.*
