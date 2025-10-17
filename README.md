# E-Commerce Delivery Prediction 🚚

## Project Overview  
This project aims to predict whether a product from an international e-commerce company will reach the customer **on time** or **not**. The company sells electronic products, and we use machine learning techniques to analyse delivery logistics, customer behaviour, product characteristics, and then build predictive models for timely delivery.


---

## Data & Features  
- **Observations:** 10,999 deliveries  
- **Features include:**  
  - `Warehouse_block` – which warehouse block (A/B/C/D/E) the shipment originated from  
  - `Mode_of_Shipment` – shipment mode (Ship / Flight / Road)  
  - `Customer_care_calls` – number of calls made by customer enquiring about the shipment  
  - `Customer_rating` – customer rating (1 lowest → 5 highest)  
  - `Cost_of_the_Product` – cost in USD  
  - `Prior_purchases` – number of prior purchases by this customer  
  - `Product_importance` – categorical (low, medium, high)  
  - `Gender` – customer gender (Male, Female)  
  - `Discount_offered` – discount (%) offered on this product  
  - `Weight_in_gms` – weight of product in grams  
- **Target variable:** `Reached.on.Time_Y.N` — 1 = **not reached on time**, 0 = **reached on time**

---

## Exploratory Data Analysis (EDA)  
In this phase we:  
- Checked distributions of weight, cost, product importance.  
- Investigated how features like weight and cost vary across delivery status (on-time vs late).  
- Explored customer behaviour features (number of care-calls, prior purchases) vs delivery status.  
- Reviewed logistics variables (warehouse block, mode of shipment) vs delivery performance.  
**Key insights:**  
- Heavier items (e.g., > ~4500 g) and higher cost (> ~$250) tended to have higher rates of late deliveries.  
- More prior purchases and higher discount offered seemed to correlate with more on-time deliveries.  
- Customer care calls increase when deliveries are delayed (makes sense).  
- Some logistic features (warehouse, mode) didn’t show strong visual effect, but are still included for modelling.

---

## Preprocessing & Modelling  
### Preprocessing  
- Dropped the `ID` column (identifier only, no predictive value).  
- Verified no missing values and no duplicates.  
- Categorical variables (`Warehouse_block`, `Mode_of_Shipment`, `Product_importance`, `Gender`) were label-encoded into numeric codes.  
- Train/test split: 80% training, 20% testing (random_state = 0 for reproducibility).

### Models built  
- **Random Forest Classifier** 
- **Decision Tree Classifier**  
- **Logistic Regression**  
- **K-Nearest Neighbors (KNN)**  
We compared these to see which gave best predictive performance.

---

## Results  
- Training accuracy (approx):  
  - Random Forest: ~72.5%  
  - Decision Tree: ~69.1%  
  - Logistic Regression: ~63.6%  
  - KNN: ~77.8% (but note: might overfit)  
- On the test set, accuracy was:  
  - Decision Tree: ~69%  
  - Random Forest: ~68%  
  - Logistic Regression: ~63%  
  - KNN: ~65%  
- From classification reports:  
  - For Random Forest: class “0” (on-time) had high recall (0.89), but class “1” (late) had lower recall (0.54)  
  - For Decision Tree: class “0” recall was ~0.97 (very high), but class “1” recall ~0.49  
**Interpretation:** The model is much better at predicting “on time” than “late” in some cases. For business use you might want to improve recall of the “late” class (so you catch more delays).

---

##Author
- Divya Prakash
