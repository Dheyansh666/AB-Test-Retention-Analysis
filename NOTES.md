# Project notes – Cookie Cats A/B test (real numbers)

## Data checks
- 90,189 rows, 0 missing, 0 duplicate userids
- Groups: gate_30 = 44,700, gate_40 = 45,489 (gate_30 share 49.56%) – sample ratio test p = 0.0086 (small imbalance, mention as limitation)
- Outlier: 1 player with 49,854 rounds (next highest 2,961) → removed
- 3,994 players (4.4%) played 0 rounds → kept
- After cleaning: **90,188 players** – gate_30 44,699 / gate_40 45,489
- Mean rounds: 51.34 vs 51.30; median 17 vs 16 (Mann-Whitney p = 0.051)
- 63.1% of players played fewer than 30 rounds

## Retention
| | gate_30 | gate_40 | diff (pp) |
|---|---|---|---|
| 1-day | 44.82% | 44.23% | 0.59 |
| 7-day | 19.02% | 18.20% | 0.82 |

## Bootstrap (1,000 resamples, seed 42)
- 7-day: avg relative diff +4.52%, 95% interval [1.62%, 7.45%], P(gate_30 better) = 100%
- 1-day: avg relative diff +1.32%, 95% interval [−0.12%, 2.80%], P(gate_30 better) = 96.4%

## Chi-square
- retention_1: chi2 = 3.17, p = 0.0750 → not significant
- retention_7: chi2 = 9.92, p = 0.0016 → significant

## Recommendation
Keep gate at level 30 – moving it to 40 reduces 7-day retention by 0.82 pp (~4.5% relative).

## Resume bullet idea
- "Showed moving the gate to level 40 cut 7-day retention from 19.0% to 18.2% (chi-square p = 0.002; bootstrap 95% CI excludes 0) and recommended keeping level 30"
