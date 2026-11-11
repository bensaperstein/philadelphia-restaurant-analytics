# What Shapes a Restaurant's Yelp Rating?
### Philadelphia Restaurant Yelp Optimization Challenge · DSAC Datathon 2026

**Second place among 9 teams**

Our four-person team explored a practical question for Philadelphia restaurant owners:

> Which factors are most strongly associated with higher Yelp ratings, and which can owners realistically control?

We combined restaurant-level regression, geographic exploration, and review sentiment analysis. Our initial hypothesis emphasized operational amenities such as takeout, delivery, and outdoor seating. The final presentation instead emphasized customer engagement, review recency, and neighborhood context alongside selected amenities.

[Final presentation](https://drive.google.com/file/d/1tRuUN_woncClPXeEPMbWjLNbmYK5pRLA/view) · [Methods and findings](docs/methods-and-findings.md) · [My contribution](docs/contributions.md)

## Competition and scope

The Northwestern Data Science and Analytics Club's 2026 datathon asked teams to translate Philadelphia Yelp data into actionable recommendations in a 5–10 minute presentation.

The challenge supplied business, review, user, tip, and check-in tables from the Yelp Open Dataset. Our presentation also used US Census context to explore restaurant density and neighborhood rent patterns. The analysis was observational and focused on Philadelphia restaurants.

## Our approach

| Workstream | What it added |
| --- | --- |
| Geographic and category exploration | Maps and comparisons of restaurant locations, neighborhood context, and category ratings |
| Restaurant-level OLS regression | An interpretable model of average Yelp star ratings using restaurant and review-related information |
| Aspect-based sentiment analysis | Food, service, atmosphere, and price signals extracted from review text |
| Additional team modeling | Rounded review-level predictions and gradient-boosting/TF-IDF experiments |

The sentiment workflow used NLTK sentence tokenization, Google News Word2Vec to expand aspect keywords, and VADER to score sentences. These were team methods; I did not independently implement the NLP pipeline.

## Reported regression results

My restaurant-level ordinary least squares (OLS) analysis used an **80/20 train/test split**.

| Metric | Reported value |
| --- | ---: |
| R² | 0.21 |
| Training RMSE | 0.73 Yelp stars |
| Test RMSE | 0.71 Yelp stars |

These figures come from the original presentation. A test RMSE of 0.71 means prediction errors of that root-mean-square magnitude on the held-out portion; it is not a 71% accuracy score. Similar training and test errors alone do not rule out leakage or establish future forecasting performance.

## What we found

- Review engagement and recency featured prominently in our restaurant-level interpretation, challenging our initial amenities-first hypothesis.
- Reservations were positively associated with ratings in our analysis.
- Older and longer reviews, and “funny” engagement, appeared among the negative associations discussed in the presentation.
- The sentiment work suggested food and service were more directly reflected in review language than atmosphere and price.
- Geographic patterns gave useful context, but location did not provide a complete explanation of restaurant ratings.

These are associations within the competition analysis. They do not establish that changing a feature would cause a rating improvement.

## Recommendations

Our presentation recommended reducing friction through reservations, monitoring detailed negative feedback, and encouraging satisfied customers to leave recent reviews. It also discussed neighborhood selection and a cautious approach to delivery expansion.

I would present these as **ideas to test**, rather than proven interventions: differences in restaurant type, customer mix, and review activity can influence both the features and observed ratings.

## Team and my role

**Phoebe Chen · Daniel Overdeck · Ben Saperstein · Aric Wang**

I handled the restaurant-level OLS regression, created regression visualizations, contributed substantially to the presentation, and worked with the team to interpret findings and develop recommendations. A teammate handled most of the sentiment-analysis implementation.

**We placed second among nine teams.**

## About this repository

This is a portfolio summary of the completed datathon project, prepared for review. The original analysis has not been changed or rerun.

- The final presentation is linked above.
- [Methods and findings](docs/methods-and-findings.md) distinguish restaurant-level regression from review-level experiments.
- [Contribution notes](docs/contributions.md) distinguish my work from team methods.
- Raw Yelp data, review text, user records, and source notebooks are not redistributed here.

The retrospective write-up was prepared with AI assistance from the original presentation, problem statement, and my documented contributions. It does not establish a new analysis or change historical ownership.
