# International Football Analysis
 
Analysis of international men's football results from 1872 onwards using Python, SQL (SQLite) and pandas: Elo ratings of national teams by historical era, home advantage, and the role of penalties.
 
[![Open in Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/m1taxx/international-football-analysis/blob/main/football_elo_analysis.ipynb)
 
## Questions
 
1. Which national teams have been the strongest in each historical era (Elo rating)?
2. Do teams score more goals at home than away?
3. Do home teams score more penalties, and does this explain the home advantage?
## Key findings
 
- **Elo by era:** Italy leads 1872–1945, England 1946–1969, Brazil 1970–1989, and Spain both 1990–2009 and 2010–now. Brazil is in the top three in each of the first four eras but only 12th in 2010–now.
- **Home advantage:** among 155 teams with at least 50 home and 50 away matches (friendlies and neutral-venue matches excluded), only Barbados scores fewer goals per match at home than away. The median home/away ratio is 1.68.
- **Penalties:** among 55 teams with long histories (since 1916), 48 score more penalties per match at home (0.140 vs 0.089), but penalties make up almost the same share of goals at home and away (7.07% vs 6.65%). They explain very little of the home advantage.
## Method
 
- **Elo rating:** all teams start at 1000 and ratings are updated after every match in chronological order. Friendlies are excluded. K-factor depends on the tournament: major finals 60, qualifiers and Nations League 40, other matches 30.
- **Eras:** ratings are reset at the start of each era (1872–1945, 1946–1969, 1970–1989, 1990–2009, 2010–now), so teams are compared within the same period. Boundaries follow major changes in international football and are approximate.
- **Home advantage and penalties:** SQL (CTEs, joins, aggregation) for the queries, pandas for filtering and summary statistics.
## Data
 
Source: [International football results from 1872 to 2017 (Kaggle)](https://www.kaggle.com/datasets/martj42/international-football-results-from-1872-to-2017).
The four CSV files used (`results`, `goalscorers`, `shootouts`, `former_names`) are stored in the [`Football data`](Football%20data) folder and loaded directly by the notebook, so it runs without any local setup.
 
## How to run
 
Click the **Open in Colab** badge above and choose *Runtime → Run all*.
 
## Limitations
 
- Elo does not model home advantage or goal difference, and renamed teams (e.g. USSR and Russia) are not merged. Teams that play mostly weak opponents, such as Jersey, can rank too high. Matches decided by penalty shootouts are counted as draws.
- `goalscorers` covers only about 32% of goals recorded in `results`, so penalty counts are underestimated; only the home–away comparison within each team is reliable. Only scored penalties are recorded, so awarded penalties cannot be analysed.
- The home advantage and penalty tables describe teams with long histories and do not represent smaller national teams.
## Next steps
 
- Merge renamed teams using `former_names`.
- Test how well Elo predicts match results.
- Add visualisations in Plotly or Power BI.
