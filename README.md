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

**1. **In the Overfitting Problem tab**, note the train R² vs. test R² gap for the plain (unregularized) model. Take a screenshot.**
<img width="608" height="635" alt="image" src="https://github.com/user-attachments/assets/1d6682d0-a9e4-4531-9add-63518dbdc077" />

---
**2. **In the Ridge tab, try at least 3 different λ values in the playground.** Watch how the red (noise) bars behave differently from the blue (real) bars as λ grows. Take a screenshot at a large λ (e.g. 1.0+).**

   - Value: 0.1
  <img width="626" height="535" alt="image" src="https://github.com/user-attachments/assets/30925396-ebe9-48c1-b887-11417c37354d" />

   - Value: 0.7
  <img width="619" height="535" alt="image" src="https://github.com/user-attachments/assets/66f25eae-5d29-4c20-89cf-b5ae55fab02c" />


   - Value: 1.15
  <img width="631" height="521" alt="image" src="https://github.com/user-attachments/assets/f2e03e7e-4e96-4fd0-81c9-26657ba77b45" />

---

**3. **In the Lasso tab, try at least 3 different λ values**, and find one where at least 2 features get zeroed out while all 4 real features are still nonzero. Take a screenshot.
**
  - Value: 5.0
<img width="617" height="533" alt="image" src="https://github.com/user-attachments/assets/526c312b-de25-42cb-8303-c92ca567007a" />

 - Value: 20.0
<img width="630" height="544" alt="image" src="https://github.com/user-attachments/assets/3164b9c5-98d5-451d-a602-7792dbae2df4" />

    
 - Value: 70.0
<img width="625" height="530" alt="image" src="https://github.com/user-attachments/assets/320939e9-2513-44d2-bc1d-f1053d049aef" />

---
**4. **Record the Canonical Ridge Model's coefficients, train R², and test R².** Take a screenshot.**

 - Canonical Ridge Model Values: Train R² = 0.9861 & Test R² = 0.8926
    
  <img width="614" height="489" alt="image" src="https://github.com/user-attachments/assets/94ae7765-be40-46ff-9f68-63ad86adbb3c" />
---

**5. **Record the Canonical Lasso Model's coefficients, train R², test R², and which features got  zeroed out.** Take a screenshot.**

   - Canonical Ridge Model Values: Train R² = 0.9777 ; Test R² = 0.8760 ; Features zeroed out 2 / 8
   
<img width="622" height="526" alt="image" src="https://github.com/user-attachments/assets/bb7511f3-8441-4ae3-b976-e14081249cc9" />


--- 
6. **Fill out `A13_ReflectionQuestions.md`**, using the exact numbers from your Canonical Model
   screenshots, and submit it along with your labeled screenshots.

# Activity 13 — Reflection Questions: Regularization at Mérida Homes

**1. For the **plain (unregularized) model**, report the train R², the test R², and the exact gap between them.**

- **Train R²:** 0.9871  
- **Test R²:** 0.8851  
- **Gap:** 0.1020  

The plain linear regression model achieves an almost perfect fit on the training data, but its performance drops when tested on unseen houses. The gap of 0.102 between train and test R² is a clear indicator of **overfitting**. This happens because the model is influenced by irrelevant features such as the owner’s lucky number or paint color code. These variables do not truly explain housing prices, but the model assigns them weight due to the small dataset. As a result, the model memorizes noise instead of learning the underlying relationship, which reduces its ability to generalize.

---

**2. Report all 8 coefficients of the **Canonical Ridge Model**.**

- Size (m²): +520  
- Bedrooms: +70  
- Age (years): −90  
- Distance to downtown (km): −320  
- Street number: −40  
- Owner’s “lucky number”: +20  
- Front door paint color code: +30  
- Owner’s zodiac sign score: +40  

Ridge regression applies an L2 penalty, which shrinks all coefficients toward zero. Unlike Lasso, Ridge does not eliminate features entirely. Instead, it reduces the magnitude of both relevant and irrelevant predictors. In this case, the four real features (size, bedrooms, age, distance) remain dominant, while the noise features are reduced but still present. This demonstrates Ridge’s strength: it controls coefficient size to prevent extreme values, stabilizing the model without discarding information.

---

**3. Report the **Canonical Ridge Model's** train R² and test R². Is the test R² better or worse than the plain model's test R² from Question 1?**

- **Train R²:** 0.9861  
- **Test R²:** 0.8926  

Compared to the plain model, Ridge slightly lowers the training R² (from 0.9871 to 0.9861) but improves the test R² (from 0.8851 to 0.8926). This trade-off is desirable: the model sacrifices a tiny bit of fit on training data to achieve **better generalization**. Ridge reduces the influence of irrelevant features, which helps the model perform more consistently on unseen houses. The improvement in test R² confirms that Ridge is effective at mitigating overfitting.

---

**4. Report all 8 coefficients of the **Canonical Lasso Model**, and name exactly which feature(s) were driven to zero.**

- Size (m²): +500  
- Bedrooms: +60  
- Age (years): −80  
- Distance to downtown (km): −300  
- Street number: −30  
- Owner’s “lucky number”: **0 (zeroed out)**  
- Front door paint color code: **0 (zeroed out)**  
- Owner’s zodiac sign score: +40  

**Zeroed-out features:** Owner’s “lucky number” and Front door paint color code.  

Lasso regression applies an L1 penalty, which not only shrinks coefficients but can drive some of them exactly to zero. This makes Lasso a powerful tool for **feature selection**. In this case, two irrelevant features were eliminated, simplifying the model and making it more interpretable. The remaining coefficients highlight the true drivers of housing prices, while noise variables are discarded.

---

**5. Report the **Canonical Lasso Model's** train R² and test R².**

- **Train R²:** 0.9777  
- **Test R²:** 0.8760  

The Lasso model has slightly lower R² values compared to Ridge. However, its advantage lies in interpretability: by removing irrelevant features, the model becomes easier to explain and avoids misleading conclusions. In practice, this trade-off is valuable when clarity and simplicity are as important as predictive accuracy.

---

**6. In your own words, explain the key difference between how **Ridge** and **Lasso** treat coefficients as λ grows, based on what you saw in the bar charts.**

- **Ridge (L2):** Shrinks all coefficients smoothly toward zero but never eliminates them. Every feature remains in the model, though irrelevant ones are heavily reduced. Ridge is best when all features may contain some signal, even if weak.  
- **Lasso (L1):** Can shrink some coefficients all the way to zero, effectively removing irrelevant features. This makes Lasso useful for **automatic feature selection**, especially when dealing with many predictors.  

In the bar charts, Ridge reduced the red bars (noise features) but kept them visible, while Lasso erased two of them completely. This difference highlights Ridge’s role in controlling magnitude versus Lasso’s role in simplifying the model.

---

**7. True or False: increasing λ always improves test R². Justify your answer using your own playground exploration (report at least one λ value where this was NOT the case).**

- **False.**  
During playground exploration, when λ was set to 1.15 in Ridge, the test R² dropped to 0.6367, which is worse than the plain model. This shows that too much regularization can harm performance by oversimplifying the model.  
Moderate λ values improve generalization, but excessive λ penalizes useful features too strongly. The key is finding a balance where the model is neither overfitting nor underfitting. Regularization is not about maximizing λ but about tuning it to the right level.

---

**8. Name one **real business or IT scenario** (other than house pricing) where you'd worry about a model overfitting due to too many irrelevant features. Which regularization type (L1 or L2) would you reach for first, and why?**
A real-world example is a customer churn prediction model in telecommunications. Companies often collect hundreds of variables (e.g., billing details, call durations, customer demographics, marketing campaigns). Many of these features may be irrelevant or redundant.  

- If too many irrelevant predictors are included, the model risks overfitting, predicting churn based on noise instead of meaningful patterns.  
- **Preferred regularization:** Lasso (L1), because it can automatically eliminate irrelevant features, leaving only the most predictive ones. This improves interpretability and reduces complexity, which is critical in business decision-making.  

Another example is frud detection in banking, where models may be flooded with irrelevant transaction metadata. Lasso helps focus only on the strongest signals of fraud, while Ridge would keep everything but shrink them. In IT, this distinction matters: Ridge stabilizes models with correlated predictors, while Lasso simplifies models with too many irrelevant variables.

--- 
# References:
- [Streamlit documentation](https://docs.streamlit.io/)
- [Markdown Guide](https://www.markdownguide.org/basic-syntax/)
