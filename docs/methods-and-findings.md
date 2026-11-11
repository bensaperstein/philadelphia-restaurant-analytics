# Methods and findings

[Back to overview](../README.md)

## Data and question

The challenge supplied five Philadelphia-focused tables derived from the Yelp Open Dataset: business, review, user, tip, and check-in information. Business and user identifiers provided links between tables. Our presentation also drew on US Census context for maps and neighborhood rent comparisons.

Our objective was to explain associations with Yelp ratings and propose decisions restaurant owners could explore. An average business rating and an individual review's star score are different outcomes; the project included analyses at both levels.

## Restaurant-level OLS

I modeled **average restaurant Yelp ratings** using ordinary least squares regression. The final slides report an 80/20 train/test split, R² of 0.21, training RMSE of 0.73 stars, and test RMSE of 0.71 stars.

The R² indicates substantial variation remains unexplained. The supplied slides do not identify a separate held-out R², so this repository does not label 0.21 as a test-set statistic.

Our interpretation emphasized engagement metrics, review recency, neighborhood context, and reservations. We discussed positive associations with “cool” engagement and recent activity, and negative associations with older reviews, longer review text, and “funny” engagement.

The presentation's proposed explanations—such as memorable experiences or sarcasm—are interpretations, not directly measured mechanisms. This write-up does not assert significance levels, coefficient magnitudes, or a fully audited feature ranking beyond the saved evidence.

## Team sentiment analysis

The team used Word2Vec embeddings to expand seed vocabulary for food, service, atmosphere, and price. Reviews were split into sentences using NLTK. VADER polarity was assigned to an aspect when matching aspect terms appeared, then aggregated into review-level scores. The slides describe joblib parallel processing.

The team explored linear predictions of individual review stars, rounding predictions, and gradient-boosting/TF-IDF approaches. The slides mention LightGBM and describe performance as limited; they do not supply a sufficiently clear comparable metric for a stronger numerical claim here.

Review-level rounding experiments are separate from my restaurant-level OLS model. The OLS test RMSE should not be attributed to the sentiment or boosting pipeline.

## Geographic and category exploration

The presentation compared restaurant density with neighborhood rent context and mapped ratings geographically. It also compared categories, discussing lower ratings for traditional American and pizza restaurants and a possible breakfast/brunch opportunity. These are descriptive patterns, not evidence that moving or changing cuisine would improve a business's rating.

## Recommendations in context

The final presentation proposed reservations, prompt attention to long negative reviews, recent customer feedback, neighborhood selection, and caution around delivery expansion.

These suggestions were not evaluated in an experiment or deployed with a restaurant. No realized revenue gain, customer growth, or rating improvement is claimed.

## Interpretation limits

- Yelp reviewers are a selected subset of customers.
- Ratings, review text, engagement, and review aggregates may overlap in how they are generated.
- Review-to-rating leakage and shared restaurants/users across splits require scrutiny before stronger prediction claims.
- A random split does not establish performance on future reviews or a new city.
- Correlated predictors complicate “most important factor” interpretations.
- Feature importance and regression associations are not causal effects.
- Similar training/test RMSE is insufficient to conclude there is no overfitting.

This repository records the project as completed; it does not repair, rerun, or retrospectively upgrade the evaluation.
