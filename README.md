# 🏨 Booking Cancellation Prediction for INN Hotels Group

## 🧩 Problem Statement

A substantial number of hotel bookings at INN Hotels Group are canceled or result in no-shows, primarily due to flexible cancellation policies and changing customer preferences. These disruptions lead to significant operational and revenue losses. The objective is to develop a data-driven solution capable of identifying potential cancellations in advance.

---

## 📊 Business Context

**Client:** INN Hotels Group, Portugal  
**Challenge:** High volume of booking cancellations leading to revenue leakage, suboptimal inventory utilization, and operational inefficiencies.  
**Solution Objective:** Leverage historical booking data to build a classification model capable of predicting cancellation likelihood.  

**Strategic Impact:**
- Improved pricing and promotional strategies  
- More accurate forecasting and room allocation  
- Reduced dependency on costly last-minute recovery efforts  

---

## 🎯 Project Goal

The primary goal is to predict whether a hotel booking will be canceled, based on customer and booking attributes. This would empower hotel management to proactively implement policies that minimize losses and optimize operations.

---

## 🧠 Approach

1. **Data Cleaning & EDA:** Conduct exploratory data analysis to identify key drivers of cancellations.
2. **Feature Engineering:** Process variables such as `lead_time`, `market_segment_type`, and past cancellation history.
3. **Modeling:** Train a **Logistic Regression** model using 70% of the data.
4. **Evaluation Metrics:** Assess model performance using accuracy, precision, and recall.
5. **Business Recommendations:** Translate model insights into actionable strategies.

---

## 🔍 Lead Business Questions & Insights
<details>
<summary>Click to view Questions</summary>
---

### Q1️. What is the average room price?

**💡 Answer:** The average room price is **€103.42**.

---

### Q2️. How do cancellations vary by market segment type and by lead time?

**💡 Answer:** 
- Cancellations are highest for Online bookings and bookings with long lead times.  
- Corporate and complementary segments are more reliable.

<details>
<summary>Click to view full analysis</summary>

#### 📊 Market Segment vs. Cancellation Rate

- **Online:** 36.5% cancellations
- **Offline:** 30% cancellations
- **Aviation:** 29.6% cancellations
- **Corporate:** ~11% cancellations (most reliable)
- **Complementary:** 0% cancellations (likely internal or comped)

#### ⏱️ Lead Time vs. Cancellation Rate

- **Longer lead time → higher cancellation rate**
- Bookings with lead time >180 days show ~74% cancellation rate.
- Lead time is positively correlated with cancellation likelihood.
- Guests booking far in advance often cancel or change plans later.

</details>

---

### Q3️. Build a logistic regression model to predict cancellations using 70% training data.

**💡 Answer:** A Logistic Regression model was trained on 70% of the data. Here's the model summary:

<details>
<summary>Click to view full model details</summary>

<table style="border-collapse: collapse; font-family: Arial, sans-serif; font-size: 13.5px;">
  <thead>
    <tr>
      <th colspan="2" style="padding: 6px 12px; border: 1px solid #ccc;"> Model Summary — Logistic Regression</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td style="padding: 4px 10px; border: 1px solid #ccc;">Model Name</td>
      <td style="padding: 4px 10px; border: 1px solid #ccc;">Logistic Regression</td>
    </tr>
    <tr>
      <td style="padding: 4px 10px; border: 1px solid #ccc;">Training Set Shape</td>
      <td style="padding: 4px 10px; border: 1px solid #ccc;">(25,293 × 21) — 70%</td>
    </tr>
    <tr>
      <td style="padding: 4px 10px; border: 1px solid #ccc;">Testing Set Shape</td>
      <td style="padding: 4px 10px; border: 1px solid #ccc;">(10,840 × 21) — 30%</td>
    </tr>
  </tbody>
</table>

---
</details>

---

### Q4. How do cancellations vary by market segment type and by lead time?

**💡 Answer:** Here are the key drivers & their relationship with the booking cancellation status.  

<details>
<summary>Click to view full analysis</summary>

#### 📊 Key Drivers - Coefficients & Relationship
<div style="text-align: left; width: fit-content;">
  <table style=" border-collapse: collapse; font-family: Arial, sans-serif; font-size: 13.5px;">
    <thead>
      <tr>
        <th colspan="3" style="padding: 6px 12px; border: 1px solid #ccc;">Logistic Regression Coefficients — Key Drivers</th>
      </tr>
      <tr>
        <th style="padding: 4px 10px; border: 1px solid #ccc;">Feature</th>
        <th style="padding: 4px 10px; border: 1px solid #ccc;">Coeff</th>
        <th style="padding: 4px 10px; border: 1px solid #ccc;">Impact</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">no_of_special_requests</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">+1.18</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Guests with custom requests show higher commitment</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">market_segment_type_Offline</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">+0.96</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Offline bookings (via travel agents / phone calls / visit to front-desk) seldom cancel</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">repeated_guest</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">+0.29</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Returning guests are more dependable</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">no_of_previous_bookings_not_canceled</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">+0.20</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Guests with a solid history of non-cancellations are trusted bookers</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">lead_time</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">−1.34</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Longer lead time increases cancellation risk — future plans change</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">avg_price_per_room</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">−0.64</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Higher prices may discourage follow-through</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">no_of_weekend_nights</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">−0.12</td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Weekend plans are more flexible, hence more cancellations</td>
      </tr>
    </tbody>
  </table>
</div>

</details>

---

### Q5. What is the model accuracy, precision, and recall?

<details>
<summary>Click to view full analysis</summary>

#### 📊 Classification Report:
<div style="text-align: left; width: fit-content;">
  <table style="border: 1px solid #ccc; border-collapse: collapse; font-family: Arial, sans-serif; font-size: 14px;">
    <thead>
      <tr>
        <th colspan="2" style="padding: 6px 12px; border: 1px solid #ccc;">Logistic Regression Summary</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;"><strong>Model</strong></td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">Logistic Regression</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;"><strong>Iterations</strong></td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">max_iter = 2500</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;"><strong>Accuracy</strong></td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">80.0%</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;"><strong>Precision</strong></td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">82.5%</td>
      </tr>
      <tr>
        <td style="padding: 4px 10px; border: 1px solid #ccc;"><strong>Recall</strong></td>
        <td style="padding: 4px 10px; border: 1px solid #ccc;">89.2%</td>
      </tr>
    </tbody>
  </table>
</div>

</details>

---

### Q6. What recommendations would you make to the management of the hotel as a data scientist based on your data analysis and predictive model (as related to cancellations)?

💡 Answer: I as a Data Scientist would give the following Recommendations-:
- Incentivize Early Bookings to Reduce Cancellations (Lead-Time Trouble)
- Boost Repeat Bookings with Family-Friendly Perks (Low Repeat Customer Problem)
- ✈Strengthen Coordination with Travel & Aviation Partners (Market Segment Complication)
- Leverage Offline Bookings to Strengthen Show-Up Rates (Offline Booking Muddle)
- Implement a Predictive Red-Flag System (Data-Science Solution)

<details>
<summary>Click to view full analysis</summary>

#### Detailed Insights:

<html lang="en">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
</head>
<body>

  <h1>Hotel Booking Cancellation: Data-Driven Recommendations</h1>

  <div class="recommendation">
    <h2>1. 🎁 Incentivize Early Bookings to Reduce Cancellations <i><u>(Lead-Time Trouble)</u></i></h2>
    <p><span class="highlight-label">Insight:</span> Guests who book far in advance (e.g., &gt;180 days) show a higher cancellation rate.</p>
    <p><span class="highlight-label">Recommendation:</span> Offer attractive, low-cost incentives to encourage commitment from early bookers:</p>
    <ul>
      <li>Complimentary spa service for bookings made &gt;6 months in advance</li>
      <li>Flexible check-in/check-out times</li>
      <li>Room upgrade (subject to availability)</li>
      <li>Early bird discounts or complimentary meals</li>
    </ul>
  </div>

  <div class="recommendation">
    <h2>2. 👨‍👩‍👧 Boost Repeat Bookings with Family-Friendly Perks <i><u>(Low Repeat Customer Problem)</u></i></h2>
    <p><span class="highlight-label">Insight:</span> The percentage of repeat guests is currently low.</p>
    <p><span class="highlight-label">Recommendation:</span> Offer returning families a <strong>complimentary kids’ room</strong>. This adds high perceived value while staying cost-effective, as only a small share of guests travel with children.</p>
  </div>

  <div class="recommendation">
    <h2>3. ✈️ Strengthen Coordination with Travel & Aviation Partners <i><u>(Market Segment Complication)</u></i></h2>
    <p><span class="highlight-label">Insight:</span> Bookings from travel agencies or aviation partners are prone to cancellation due to flight issues or overbooking.</p>
    <p><span class="highlight-label">Recommendation:</span> Coordinate closely with agents. For confirmed travel groups, offer:</p>
    <ul>
      <li>Free airport pick-up and drop</li>
      <li>Bulk booking discounts</li>
      <li>Priority check-in for tour groups</li>
    </ul>
  </div>

  <div class="recommendation">
    <h2>4. 📞 Leverage Offline Bookings to Strengthen Show-Up Rates <i><u>(Offline Booking Muddle)</u></i></h2>
    <p><span class="highlight-label">Insight:</span> Offline bookings (via phone, front desk, or agents) show lower cancellation rates — likely due to greater effort and intention.</p>
    <p><span class="highlight-label">Recommendation:</span> Stay in touch with offline guests via SMS or email. Offer arrival perks like:</p>
    <ul>
      <li>Welcome drink</li>
      <li>Room upgrade (if available)</li>
      <li>Discount coupon for future stay</li>
    </ul>
  </div>

  <div class="recommendation">
    <h2>5. 🚦 Implement a Predictive Red-Flag System <i><u>(Data-Science Solution)</u></i></h2>
    <p><span class="highlight-label">Insight:</span> Some customers consistently show a high probability of cancelling.</p>
    <p><span class="highlight-label">Recommendation:</span> Use model predictions to tag bookings with a “Red Flag.” For these:</p>
    <ul>
      <li>Apply stricter cancellation terms or partial prepayment</li>
      <li>Notify staff to confirm bookings or follow up</li>
    </ul>
  </div>
</details>

</details>

---

## 📁 About the Dataset

- **Source:** Proprietary dataset from INN Hotels Group  
- **File:** [INNHotelsGroup.csv](INNHotelsGroup.csv) 
- **Features:** 19 input features, 1 binary target (`booking_status`)  
- **Granularity:** Booking records  

---

## 📘 Metadata Dictionary

<details>
<summary>Click to view column descriptions</summary>

| Column Name                        | Description |
|------------------------------------|-------------|
| `Booking_ID`                       | Unique identifier of each booking |
| `no_of_adults`                     | Number of adults included in the booking |
| `no_of_children`                   | Number of children included in the booking |
| `no_of_weekend_nights`            | Number of weekend nights (Saturday/Sunday) booked |
| `no_of_week_nights`               | Number of weekday nights (Monday–Friday) booked |
| `type_of_meal_plan`               | Type of meal plan selected (None, Meal Plan 1/2/3) |
| `required_car_parking_space`      | Parking space required (1 = Yes, 0 = No) |
| `room_type_reserved`              | Encoded room type reserved |
| `lead_time`                       | Days between booking and arrival |
| `arrival_year`                    | Year of arrival |
| `arrival_month`                   | Month of arrival |
| `arrival_date`                    | Day of the month for arrival |
| `market_segment_type`             | Market segment type (e.g., Online, Offline, Corporate) |
| `repeated_guest`                  | Whether the customer is a repeat guest (1 = Yes) |
| `no_of_previous_cancellations`   | Count of past cancellations by the guest |
| `no_of_previous_bookings_not_canceled` | Count of past completed bookings by the guest |
| `avg_price_per_room`              | Average price per room for the booking |
| `no_of_special_requests`          | Count of special room requests |
| `booking_status`                  | Target variable – 1 if canceled, 0 if not |
</details>

---





</body>
</html>

</details>

</details>



