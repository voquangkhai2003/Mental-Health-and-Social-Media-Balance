# 🧠 Mental Health & Social Media Balance Analysis

> An exploratory data analysis project investigating the relationship between social media usage, screen time, and mental health indicators — using statistical hypothesis testing and visualization to extract actionable insights from 500 user records.

---

## 📌 Project Overview

This project examines how daily social media and screen time habits relate to mental wellbeing metrics — specifically stress, sleep quality, and happiness — across different age groups, genders, and platforms. The analysis goes beyond simple visualizations by applying formal statistical tests to validate observed patterns.

| | |
|---|---|
| **Dataset** | Mental Health & Social Media Balance (synthetic) |
| **Records** | 500 users (477 after filtering) |
| **Target metrics** | Stress Level · Sleep Quality · Happiness Index |
| **Approach** | EDA → Feature Engineering → Statistical Testing → Visualization |

---

## 🗂️ Dataset

**File:** `Mental_Health_and_Social_Media_Balance_Dataset.csv` — 500 rows × 10 columns

| Column | Type | Description |
|---|---|---|
| `User_ID` | str | Unique user identifier |
| `Age` | int | Age (range: 16–49) |
| `Gender` | str | Male / Female / Other |
| `Daily_Screen_Time(hrs)` | float | Daily screen time in hours (avg: 5.5h, max: 10.8h) |
| `Sleep_Quality(1-10)` | float | Self-reported sleep quality score |
| `Stress_Level(1-10)` | float | Self-reported stress score |
| `Days_Without_Social_Media` | float | Days per week without social media |
| `Exercise_Frequency(week)` | float | Workout sessions per week |
| `Social_Media_Platform` | str | Primary platform used |
| `Happiness_Index(1-10)` | float | Self-reported happiness score |

### Dataset Overview

| Metric | Value |
|---|---|
| Age range | 16 – 49 (mean: 33) |
| Avg screen time | 5.5 hrs/day |
| Avg stress level | 6.6 / 10 |
| Avg sleep quality | 6.3 / 10 |
| Avg happiness | 8.4 / 10 |

**Gender split:** Male 49.6% · Female 45.8% · Other 4.6% (excluded from gender comparisons)

**Platform distribution:**

| Platform | Users |
|---|---|
| TikTok | 95 |
| X (Twitter) | 88 |
| LinkedIn | 87 |
| Facebook | 81 |
| YouTube | 75 |
| Instagram | 74 |

---

## 🔄 Project Pipeline

```
Raw Dataset (500 records)
        │
        ▼
1. Data Profiling          ← ydata_profiling auto report (HTML)
        │
        ▼
2. Cleaning & Casting      ← Filter 'Other' gender, fix dtypes
        │
        ▼
3. Feature Engineering     ← ScreenTime_Group · Age_Group · High_Stress flag
        │
        ▼
4. Exploratory Analysis    ← Group summaries, correlations, cross-tabs
        │
        ▼
5. Statistical Testing     ← Chi-square · ANOVA · Kruskal-Wallis · T-test
        │
        ▼
6. Visualization           ← Heatmap · Violin · Jointplot · Pairplot · Interaction plots
```

---

## ⚙️ Feature Engineering

Three derived features were created to enable segment-level analysis:

| Feature | Definition |
|---|---|
| `ScreenTime_Group` | Low (<3h) / Medium (3–6h) / High (>6h) |
| `Age_Group` | 18–25 / 26–35 / 36–45 / 46+ |
| `High_Stress` | Binary flag: 1 if `Stress_Level ≥ 8`, else 0 |
| `Exercise group` | 0 / 1–2 / 3–4 / 5+ sessions per week |

---

## 📐 Statistical Tests Applied

| Test | Hypothesis | Variables |
|---|---|---|
| **Pearson Correlation** | Linear relationship between numeric variables | All numeric columns vs. Happiness & Stress |
| **Chi-square test** | Association between platform and high stress | `Social_Media_Platform` × `High_Stress` |
| **One-way ANOVA** | Mean stress differs across age groups | `Stress_Level` by `Age_Group` |
| **Kruskal-Wallis** | Non-parametric alternative to ANOVA (no normality assumption) | `Stress_Level` by `Age_Group` |
| **Welch's T-test** | Screen time differs between high- vs. low-stress users | `Daily_Screen_Time` × `High_Stress` |

---

## 📊 Visualizations

| Chart | Purpose |
|---|---|
| **Heatmap** | Correlation matrix across all numeric variables |
| **Violin plot** | Stress distribution by gender (with quartile markers) |
| **Jointplot with regression** | Screen time vs. stress — scatter + marginal distributions + regression line |
| **Boxplot + Stripplot** | Happiness distribution across exercise frequency groups |
| **Interaction plot** | Exercise group × Gender interaction on stress (point plot) |
| **Pairplot** | Pairwise relationships across all 7 numeric variables (300-sample) |

---

## 💡 Key Insights

1. **Screen time is the strongest negative predictor of happiness** (r = –0.71) — users averaging >6h/day score significantly lower on happiness and higher on stress than low-usage peers.
2. **Stress is the strongest negative predictor of happiness** (r = –0.74) — the two metrics are tightly coupled, suggesting that stress reduction directly drives wellbeing improvements.
3. **Sleep quality has a strong positive correlation with happiness** (r = +0.68) — reinforcing that sleep is a critical lever in mental health alongside screen time reduction.
4. **Platform choice correlates with stress** — the Chi-square test examines whether TikTok and X (Twitter) users show disproportionately high stress rates vs. LinkedIn or YouTube users.
5. **Exercise frequency moderates stress differently by gender** — the interaction plot reveals non-uniform benefits across genders, suggesting gender-tailored wellness recommendations.
6. **Age group differences in stress** — ANOVA and Kruskal-Wallis tests assess whether younger vs. older users experience meaningfully different stress levels despite similar screen time.
7. **Days without social media has weak correlation with happiness** (r = +0.06) — suggesting that simply taking breaks is insufficient without addressing underlying screen time habits.

---

## 📁 File Structure

```
├── Mental_Health_and_Social_Media_Balance.ipynb        ← Full analysis notebook
└── Mental_Health_and_Social_Media_Balance_Dataset.csv  ← Dataset (500 rows × 10 columns)
```

---

## ⚙️ Installation & Usage

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels ydata-profiling
jupyter notebook Mental_Health_and_Social_Media_Balance.ipynb
```

> **Note:** The `ydata_profiling` report generates a standalone HTML file (`mental_health_social_media_balance_report.html`) with a full automated EDA summary — run Cell 2 to regenerate it.

---

## 🛠️ Tech Stack

| Category | Tools |
|---|---|
| Language | Python 3 |
| Data wrangling | `pandas`, `numpy` |
| Visualization | `matplotlib`, `seaborn` |
| Statistics | `scipy.stats` (Chi-square, ANOVA, Kruskal-Wallis, T-test), `statsmodels` |
| Auto-profiling | `ydata_profiling` |

---

## 👤 Author

**Vo Quang Khai**
Data Analyst | Finance & Data Science Background
[LinkedIn](https://www.linkedin.com/in/voquangkhaikg2003/) · [GitHub](https://github.com/voquangkhai2003)
