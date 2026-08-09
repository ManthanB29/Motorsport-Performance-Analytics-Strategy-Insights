# Motorsport Performance Analytics & Strategy Insights (Formula 1) — Exploratory Data Analysis (1950–2024)

A comprehensive exploratory data analysis of 75 years of Formula 1 racing — covering 1,100+ races, 800+ drivers, and 200+ constructors across 9 interconnected datasets. The goal was to move beyond surface-level leaderboards and uncover the structural patterns that actually determine performance, consistency, and dominance in F1.


## Key Findings


### Driver Performance
| Metric | Finding |
|--------|---------|
| All-Time Points Leader | Lewis Hamilton — 4,820.5 pts across career |
| Most Efficient Winner | Juan Fangio — 41.4% win rate among regular competitors |
| Most Consistent Front Runner | Lewis Hamilton — 5.55 std dev in finishing position |
| Closest Championship Ever | 1984: Niki Lauda beat Alain Prost by just **0.5 points** |
| Best Single Season | Max Verstappen 2023 — 530 points (highest in modern era) |

> **Insight**: Hamilton's dominance is not just volumetric — he leads in both raw output *and* consistency metrics, suggesting sustained excellence rather than era-specific advantage. Fangio's win ratio remains unmatched despite competing in an era with 7–9 races per season and DNF rates exceeding 60%.


### Constructor Intelligence
| Metric | Finding |
|--------|---------|
| Most Wins (All-Time) | Ferrari — 249 wins across 7 decades |
| Hybrid Era Dominance | Mercedes — 129 wins, Red Bull — 122 wins |
| Most Reliable | Brawn GP — lowest DNF ratio in dataset |
| Biggest YoY Improvement | Mercedes 2014 — +341 points (hybrid regulation shift) |
| Street Circuit Benchmark | Brawn GP — 2.75 avg finish on street circuits |

> **Insight**: Ferrari's lead reflects longevity, not peak dominance — Mercedes and Red Bull compressed comparable win counts into fewer seasons. Brawn's 2009 season stands as the most efficient single-season performance in the dataset: highest win ratio, lowest DNF rate, near-perfect qualifying-to-finish conversion.


### Circuit & Strategic Intelligence

**Qualifying matters — but less than expected**
- Pole-to-win conversion rate: **42.8%** — meaningful but far from deterministic
- Qualifying-to-finish correlation: **r = 0.446** — grid position explains ~20% of race outcome variance
- Circuits amplify this effect: Yas Marina (68.8%), Marina Bay (66.7%), Barcelona (65.4%) heavily reward front-row starts due to limited overtaking geometry

**Pit stop strategy is widely misunderstood**
- Pit stop *count* vs finish position: **r = 0.039** (near-zero correlation)
- Conclusion: *when* and *why* you pit matters far more than how many times or how fast — tire strategy and track position dominate pit stop speed

**Circuit character shapes outcomes**
| Circuit Trait | Example | Implication |
|--------------|---------|-------------|
| Fastest avg lap | Red Bull Ring (74.2s) | Low-downforce setup critical |
| Highest variance | Mugello (60,324 ms²) | Weather/safety car sensitive |
| Hardest to overtake | Istanbul / Bahrain / Shanghai | Qualifying premium elevated |
| Most unpredictable | Sochi (37.5% unique winner ratio) | Strategy lottery |


### Historical Reliability Trend

F1 reliability has undergone a **5–6x structural improvement** over 75 years:

| Era | Avg DNF Rate | Character |
|-----|-------------|-----------|
| 1980s | ~60–70% | Mechanical chaos, attrition racing |
| 1990s | ~45–50% | Improving but volatile |
| 2000s | ~30% | Modern standards emerging |
| 2010s | ~18% | Hybrid reliability era |
| 2020s | ~12–15% | Engineering maturity |

> This is not just an engineering story — it fundamentally changed race strategy. When DNF rates were high, attrition *was* the strategy. Modern F1 is won on pace and pit timing, not survival.


## Project Structure
```
Formula1_EDA/
│
├── Formula1_EDA.ipynb                          # Main analysis notebook
├── README.md                         # Project overview
│
└── formula-1-world-championship-1950-2020.zip                        # Dataset (9 CSV files)
```

## Analysis Sections

| Section | Key Questions Answered |
|---------|----------------------|
| **Driver Analysis** | Leaderboards, win ratios, consistency scoring, circuit specialization, street circuit performance |
| **Constructor Analysis** | Team dominance, YoY improvement, qualifying vs race conversion, DNF reliability |
| **Circuit Analysis** | Race frequency, lap time distribution, overtaking difficulty, pole position advantage, predictability scoring |
| **Qualifying & Race Performance** | Pole-to-win rate, grid-finish correlation, position conversion efficiency by segment |
| **Pit Stop Analysis** | Speed benchmarks, consistency scoring, strategic impact on race outcome |
| **Reliability & Attrition** | DNF trends by driver/constructor/circuit/era, historical reliability evolution |
| **Season & Historical Trends** | Calendar growth, lap time evolution, championship competitiveness, dominance ratios |


## Methodology Notes

**Outlier handling**: Driver comparisons use IQR-based filtering to exclude extremely short or long careers from ratio metrics (win rate, avg finish), ensuring comparisons reflect sustained competitive participation rather than single-race anomalies.

Constructor filtering is done on the basis of participation in atleast one season.

**Segmentation**: Drivers and constructors are segmented into *Front Runners* (avg qualifying position ≤ 5) and *Midfield* (avg qualifying position 5–15) before consistency analysis — because a 3.0 std dev means something very different for a race winner vs a points scorer.

**DNF classification**: Any result status not containing "Finished" or "+N laps" is classified as a DNF, capturing mechanical failures, accidents, and disqualifications.

## Dataset

**Source**: [Formula 1 World Championship (1950–2020)](https://www.kaggle.com/datasets/rohanrao/formula-1-world-championship-1950-2020) — Kaggle

**Note** : Even though the dataset is named as "1950-2020", it contains data till 2024.

**Coverage**: 1950–2024 | 9 relational CSV files | 1,100+ races


## Libraries Used

```
python
pandas
numpy
matplotlib
seaborn
```
