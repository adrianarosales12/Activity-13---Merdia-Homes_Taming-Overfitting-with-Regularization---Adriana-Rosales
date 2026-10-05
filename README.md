# Activity 13: Mérida Homes — Taming Overfitting with Regularization
## Sessions 23
## Due date (mm/dd/yyyy): 10/18/2026
## Adriana Rosales González
## Delivery Format: [] Video URL | [X] Markdown file | [] Jupyter Notebook file

---

## The Story

**Mérida Homes** gave you a messier spreadsheet this time. Alongside the 4 features that
genuinely predict price (size, bedrooms, age, distance), someone also included 4 columns that
have **nothing to do with price**: a street number, the owner's "lucky number," a paint color
code, and a zodiac score. Worse, you only have 20 training houses to learn from (30 more are
held back to test how well the model generalizes).

That combination — a small training set and several irrelevant features — is exactly what
causes a linear regression model to **overfit**: fitting noise in the training data instead of
the real underlying pattern. **Regularization** is how you fix that.

--- 

### Your Tasks

1. **In the Overfitting Problem tab**, note the train R² vs. test R² gap for the plain
   (unregularized) model. Take a screenshot.

2. **In the Ridge tab, try at least 3 different λ values in the playground.** Watch how the red
   (noise) bars behave differently from the blue (real) bars as λ grows. Take a screenshot at a
   large λ (e.g. 1.0+).

3. **In the Lasso tab, try at least 3 different λ values**, and find one where at least 2
   features get zeroed out while all 4 real features are still nonzero. Take a screenshot.

4. **Record the Canonical Ridge Model's coefficients, train R², and test R².** Take a screenshot.

5. **Record the Canonical Lasso Model's coefficients, train R², test R², and which features got
   zeroed out.** Take a screenshot.


--- 
6. **Fill out `A13_ReflectionQuestions.md`**, using the exact numbers from your Canonical Model
   screenshots, and submit it along with your labeled screenshots.

---
# Activity 13 — Reflection Questions: Regularization at Mérida Homes
1. For the **plain (unregularized) model**, report the train R², the test R², and the exact gap between them.

2. Report all 8 coefficients of the **Canonical Ridge Model**.

3. Report the **Canonical Ridge Model's** train R² and test R². Is the test R² better or worse than the plain model's test R² from Question 1?

4. Report all 8 coefficients of the **Canonical Lasso Model**, and name exactly which feature(s) were driven to zero.

5. Report the **Canonical Lasso Model's** train R² and test R².

6. In your own words, explain the key difference between how **Ridge** and **Lasso** treat coefficients as λ grows, based on what you saw in the bar charts.

7. True or False: increasing λ always improves test R². Justify your answer using your own playground exploration (report at least one λ value where this was NOT the case).

8. Name one **real business or IT scenario** (other than house pricing) where you'd worry about a model overfitting due to too many irrelevant features. Which regularization type (L1 or L2) would you reach for first, and why?

--- 
# References:
- [Streamlit documentation](https://docs.streamlit.io/)
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
