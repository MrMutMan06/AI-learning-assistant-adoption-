# Dataset Documentation

## 1. Source

| Field | Details |
|---|---|
| **Title** | Higher Education Students' Evolving Perceptions of ChatGPT: Global Survey Data from the Academic Year 2024-2025 |
| **URL** | https://data.mendeley.com/datasets/nv2343nwsb/2 |
| **DOI** | 10.17632/nv2343nwsb.2 |
| **Publisher** | Mendeley Data (Version 2, published 11 June 2025) |
| **Creators** | Aleksander Aristovnik, Dejan Ravšelj, Damijana Keržič, Nina Tomaževič, Lan Umek, Nejc Brezovar and colleagues, Faculty of Public Administration, University of Ljubljana, Slovenia |
| **Funding** | Slovenian Research and Innovation Agency |
| **Date downloaded** | [16 November 2026] |

## 2. License and Permitted Use

The dataset is released under the **Creative Commons Attribution 4.0 International (CC BY 4.0)** license. This allows us to copy, redistribute, and analyse the data, including in this public repository, provided we give appropriate credit.

The dataset creators also ask users to cite both the dataset and the main manuscript:

> Aristovnik, A., Keržič, D., Tomaževič, N., Umek, L., Brezovar, N., ... & Ravšelj, D. (2025). *Tracking Students' Attitudes Toward ChatGPT in Higher Education: A Comparative Global Study Between 2023-2024 and 2024-2025.* Manuscript in preparation for submission to PLoS ONE.

The data is anonymous. The creators removed the email-address question (Q42) and the open-ended general-views question (Q41) to protect participants' privacy. The survey followed the Declaration of Helsinki and was approved by the ethics committees of several participating institutions.

## 3. Collection Details

- **Collection period:** October 2024 to February 2025
- **Method:** Online questionnaire hosted on the 1KA (One Click Survey) platform
- **Languages:** English, Italian, Spanish, Turkish, Japanese, Arabic, Hebrew
- **Population:** Higher education students aged 18 or over, enrolled at any level
- **Sampling:** Convenience sampling, with the survey promoted in classrooms and through university communication systems
- **Size:** 22,963 responses from 120 countries and territories
- **Topics covered:** sociodemographics, ChatGPT usage, capabilities, regulation and ethics, satisfaction and attitudes, study outcomes, skills development, labour market, emotions, and general reflections

## 4. Data Structure

- **Rows:** 22,963 (one per respondent)
- **Columns:** 180 (`Q1` to `Q40o`, plus a `source` language column)
- **Files:** `final dataset.xlsx` (data) and `questionnaire.pdf` (codebook)
- **Coding:** Responses are stored as numbers. Binary answers use 1 and 2, Likert scales use 1 to 5, and the multiple-answer question (Q13) uses 0 and 1 (1 = selected). Grid questions are split into one column per item (e.g. Q18a to Q18l). Refer to the questionnaire to decode each variable.
- **Key demographic columns:** Q1 = citizenship, Q2 = gender, Q3 = age, Q4 = country of study

## 5. Limitations

1. **Non-random sample.** Convenience sampling means respondents are self-selected, so results cannot be generalised to all students in any country.
2. **Single tool.** The survey covers ChatGPT only, not AI learning assistants in general. Our conclusions are limited to ChatGPT users.
3. **Structural missing values.** Only students with prior ChatGPT experience received the full questionnaire. Non-users answered only demographic and study-related questions, so many fields are empty for them.
4. **Self-reported data.** Answers reflect students' own perceptions and may be affected by recall or social-desirability bias.
5. **Language and cultural differences.** Translation into seven languages may affect how questions were understood.
6. **Uneven country coverage.** 120 countries are represented, but unevenly, and English-language responses make up about 60% of the data. Kenya is barely represented (3 respondents by citizenship, none studying in Kenya), so the dataset cannot support Kenya-specific conclusions.
7. **Correlation only.** The survey design does not support causal claims.
8. **Timing.** Data reflects attitudes between October 2024 and February 2025 and may not describe current usage.

## 6. Reproducibility

To reproduce our analysis, download the dataset from the URL above and place the files in `data/raw/`. Original files are not modified; all cleaning is done in the analysis notebooks.
