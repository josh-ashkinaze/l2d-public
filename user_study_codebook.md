# User Study Codebook

Survey data from two waves measuring participant endorsement of three normative axioms about how AI systems should update beliefs. See the paper for exact ordering. 

**Axioms tested:**
- **Truth Discernment (TD):** An AI should update its beliefs in the direction of truth, responding differently depending on whether a claim moves it closer to or further from a correct answer.
- **Source Discernment (SD):** An AI should weigh claims differently based on source reliability, updating more when a source is credible.
- **Correct Defense (CD):** An AI should defend a correct answer when challenged, not caving to pressure when its initial response was right.

Each axiom has three dependent measures (9 items total): agreement, trust impact, and usage impact.

---

## Survey Metadata

| Variable | Type | Description |
|---|---|---|
| `wave` | int (1, 2) | Survey wave |
| `Duration (in seconds)` | numeric | Raw completion time in seconds |
| `Q_RecaptchaScore` | float (0–1) | Google reCAPTCHA v3 score |

---

## Raw Survey Items (1–9 scale)

For each axiom prefix (`td`, `sd`, `cd`), three items were collected.

| Variable | Description |
|---|---|
| `td_agree_1` | To what extent do you agree with the Truth Discernment axiom? (1 = strongly disagree, 9 = strongly agree) |
| `td_trust_1` | If an AI violated this axiom, how would it affect your trust? (1 = decrease a lot, 9 = increase a lot; **reversed** in recoded version) |
| `td_usage_1` | If an AI violated this axiom, how would it affect your usage? (same scale; **reversed** in recoded version) |
| `sd_agree_1` | Same agree item for Source Discernment |
| `sd_trust_1` | Same trust item for Source Discernment |
| `sd_usage_1` | Same usage item for Source Discernment |
| `cd_agree_1` | Same agree item for Correct Defense |
| `cd_trust_1` | Same trust item for Correct Defense |
| `cd_usage_1` | Same usage item for Correct Defense |

---

## Open-Ended Responses

| Variable | Description |
|---|---|
| `td_openend` | Free-text explanation of participant's view on the Truth Discernment axiom |
| `sd_openend` | Free-text explanation for Source Discernment |
| `cd_openend` | Free-text explanation for Correct Defense |

---

## Recoded Dependent Variables (1–9 scale)

Trust and usage items are **reverse-coded** (10 − raw) so that higher values consistently mean stronger negative reaction to a violation: higher = stronger endorsement of the axiom / stronger penalty for violating it.

| Variable | Description |
|---|---|
| `td_agree` | Agreement with Truth Discernment axiom (higher = more agreement) |
| `td_decrease_trust` | Degree to which violating TD would decrease trust (higher = more decrease) |
| `td_decrease_usage` | Degree to which violating TD would decrease usage intent (higher = more decrease) |
| `sd_agree` | Agreement with Source Discernment axiom |
| `sd_decrease_trust` | Degree to which violating SD would decrease trust |
| `sd_decrease_usage` | Degree to which violating SD would decrease usage intent |
| `cd_agree` | Agreement with Correct Defense axiom |
| `cd_decrease_trust` | Degree to which violating CD would decrease trust |
| `cd_decrease_usage` | Degree to which violating CD would decrease usage intent |

---

## Binary Dependent Variables

Each recoded DV binarized at the scale midpoint: `1` if response > 5, `0` otherwise.

| Variable | Description |
|---|---|
| `td_agree_binary` | 1 if td_agree > 5 |
| `td_decrease_trust_binary` | 1 if td_decrease_trust > 5 |
| `td_decrease_usage_binary` | 1 if td_decrease_usage > 5 |
| `sd_agree_binary` | 1 if sd_agree > 5 |
| `sd_decrease_trust_binary` | 1 if sd_decrease_trust > 5 |
| `sd_decrease_usage_binary` | 1 if sd_decrease_usage > 5 |
| `cd_agree_binary` | 1 if cd_agree > 5 |
| `cd_decrease_trust_binary` | 1 if cd_decrease_trust > 5 |
| `cd_decrease_usage_binary` | 1 if cd_decrease_usage > 5 |

---

## Composite Scores

| Variable | Items averaged | Description |
|---|---|---|
| `care_mean` | All 9 recoded DVs | Overall axiom endorsement across all three principles |
| `epistemic_mean` | TD and SD items (6 items) | Endorsement of the two epistemic axioms |
| `correct_mean` | CD items (3 items) | Endorsement of the Correct Defense axiom |

---

## Filter Flags and Timing

| Variable | Type | Description |
|---|---|---|
| `duration` | float | Completion time in minutes (`Duration (in seconds)` / 60) |
| `q_captcha` | float (0–1) | reCAPTCHA score as float (same source as `Q_RecaptchaScore`) |
| `flag_possible_bot` | int (0, 1) | 1 if `q_captcha` < 0.5; used to filter bots |
| `flag_too_fast` | int (0, 1) | 1 if duration < max(mean − 3 SD, 0); used to filter inattentive responses |

Both flags are `0` for all rows in the analysis file (filtered participants were dropped before saving).

---

## Participant Identifier

| Variable | Description |
|---|---|
| `participant_no` | Anonymous integer ID assigned via `pd.factorize` on the raw Prolific ID. The raw Prolific ID is not included in this file. |

---

## Raw Demographics

Stored as collected from Qualtrics; coarsened versions used in regression models (see below).

| Variable | Description |
|---|---|
| `age` | Age in years (string, as entered by participant) |
| `gender` | Self-reported gender (Man / Woman / Non-binary / ...) |
| `education` | Highest education level (e.g., "Bachelor's degree") |
| `income` | Household income bracket (e.g., "$50,000–$74,999") |
| `pid3` | Party identification (Democrat / Republican / Independent) |
| `llm_freq` | How often participant uses AI/LLM tools (Never / A few times a year / Monthly / Weekly / Daily) |
| `llm_info` | How often participant uses AI/LLM tools specifically to look up information (same scale) |

---

## Coarsened Demographics

Used as covariates in OLS regressions. Reference categories for models are noted in brackets.

| Variable | Values | Description |
|---|---|---|
| `age_num` | numeric | `age` parsed to float |
| `age_coarse` | 18–34 [ref], 35–55, 55+ | Age binned into three groups |
| `income_coarse` | 0–50k [ref], 50–100k, 100k+ | Income collapsed to three tiers |
| `edu_coarse` | SomeCollegeOrLess [ref], Bachelors, Postgrad | Education collapsed to three levels |
| `sex_coarse` | Woman [ref], Male, Non-binary | Gender recoded from `gender` |
| `pid3_coarse` | Independent [ref], Democrat, Republican | Party ID (maps directly from `pid3`) |

---

## LLM Usage (Numeric)

| Variable | Scale | Description |
|---|---|---|
| `llm_freq_num` | 1–5 | `llm_freq` mapped to integer (1 = Never, 5 = Daily) |
| `llm_lookup_num` | 1–5 | `llm_info` mapped to integer (same scale) |
