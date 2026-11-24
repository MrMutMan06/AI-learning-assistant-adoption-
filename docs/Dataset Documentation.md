## Dataset Documentation

This project uses **two survey waves** from the same global study of higher education students' perceptions of ChatGPT. Both come from the same research team and use the same questionnaire structure, so they can be combined for a comparison over time.

| | Wave 1 (2023-24) | Wave 2 (2024-25) |
|---|---|---|
| **Title** | Higher Education Students' Early Perceptions of ChatGPT: Global Survey Data | Higher Education Students' Evolving Perceptions of ChatGPT: Global Survey Data from the Academic Year 2024-2025 |
| **URL** | https://data.mendeley.com/datasets/ymg9nsn6kn/2 | https://data.mendeley.com/datasets/nv2343nwsb/2 |
| **DOI** | 10.17632/ymg9nsn6kn.2 | 10.17632/nv2343nwsb.2 |
| **Version / published** | V2, 5 February 2025 | V2, 11 June 2025 |
| **Collection period** | October 2023 - February 2024 | October 2024 - February 2025 |
| **Responses** | 23,218 | 22,963 |
| **Countries / territories** | 109 | 120 |
| **Licence** | CC BY 4.0 | CC BY 4.0 |
| **Date downloaded** | 16th novemeber 2026 |

**Combined size:** 46,181 responses (23,218 + 22,963).

**Creators (both waves):** Dejan Ravšelj, Aleksander Aristovnik, Damijana Keržič, Nina Tomaževič, Lan Umek, Nejc Brezovar and an international group of co-contributors (University of Ljubljana, Faculty of Public Administration).
**Publisher:** Mendeley Data.
**Funding (Wave 2):** Slovenian Research and Innovation Agency (grants P5-0093, J5-60095, Z5-4569, Start-up Research Programme).

### License and legal/public use
- Both datasets are publicly available on Mendeley Data without login.
- Wave 2 is licensed **CC BY 4.0**, which allows sharing and adapting the data with attribution. Wave 1's licence is stated on its dataset page (see the table above).
- Responses are anonymous. Q41 (free-text views) and Q42 (email addresses) were removed from both datasets to protect privacy.
- Participants were adults (18+) who gave voluntary consent, and the surveys were approved by the ethics committees of several participating institutions.
- The data is used here for educational purposes with full attribution to the original authors.

### Collection method
Both waves used an online questionnaire in 1KA (One Click Survey) with convenience sampling, through classroom promotion and university communication channels. Wave 2 was offered in 7 languages (EN, IT, ES, TR, JP, AR, HE) and includes a `source` column recording the language version.

### How the two waves are used together
- A `wave` column is added to each dataframe (`2023-24` and `2024-25`) before the datasets are combined.
- Column names and answer codes are checked to match across waves before merging.
- Binary answers are coded 1/2, Likert items 1-5, and the multi-select question Q13 is coded 0/1.
- The waves are different groups of anonymous students, so individuals cannot be tracked from one wave to the next. Comparisons are between groups, not within people.

### Limitations
1. **Non-random sample:** convenience sampling means results cannot be generalised to all students worldwide.
2. **Self-reported data:** answers reflect perceptions, which may be biased and may not match real behaviour.
3. **Missing values by design:** students who had never used ChatGPT only answered the sociodemographic and personal sections, so many later columns are blank for them.
4. **Uneven representation:** some countries and survey languages have far more responses than others, and Wave 2 covers more countries than Wave 1.
5. **Not a panel:** the two waves are separate samples, so differences may partly reflect who responded, not only changing attitudes.
6. **ChatGPT only:** the surveys do not cover other AI learning tools (Gemini, Claude, Copilot, etc.).
7. **Numeric coding:** answers are stored as codes, so the questionnaire is needed to interpret them.
8. **No causal claims:** this is survey data, so it shows associations, not cause and effect.
9. **Possible translation differences:** the same question may be understood slightly differently across languages.

### Citations
- Ravšelj, D., Aristovnik, A., Keržič, D., Tomaževič, N., Umek, L., Brezovar, N., et al. (2025). *Higher Education Students' Early Perceptions of ChatGPT: Global Survey Data* [Data set]. Mendeley Data, V2. https://doi.org/10.17632/ymg9nsn6kn.2
- Aristovnik, A., Keržič, D., Tomaževič, N., Umek, L., Brezovar, N., ... & Ravšelj, D. (2025). *Higher Education Students' Evolving Perceptions of ChatGPT: Global Survey Data from the Academic Year 2024-2025* [Data set]. Mendeley Data, V2. https://doi.org/10.17632/nv2343nwsb.2
- Ravšelj, D., Keržič, D., Tomaževič, N., et al. (2025). Higher education students' perceptions of ChatGPT: A global study of early reactions. *PLoS ONE, 20*(2), e0315011.
