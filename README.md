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

## 📁 About the Dataset

- **Source:** Proprietary dataset from INN Hotels Group  
- **File:** `INNHotelsGroup.csv`  
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
---

## 🔍 Lead Business Questions & Insights

---

### 1️⃣ What is the average room price?

**💡 Answer:** The average room price is **€103.42**.

---

### 2️⃣ How do cancellations vary by market segment type and by lead time?

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

### 3️⃣ Build a logistic regression model to predict cancellations using 70% training data.

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

</details>


