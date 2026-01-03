
# Restaurant Ratings Analysis

## Business Objective

Analyze restaurant ratings and consumer behavior in Mexico to identify key factors influencing customer satisfaction, dining preferences, and operational attributes that contribute to higher restaurant ratings. The insights are intended to support restaurant owners and stakeholders in improving service quality, pricing strategy, and customer experience.

---

## Table of Contents

* Case Study
* Dataset Overview
* Data Model (ER Diagram)
* Data Preparation & Feature Engineering
* Analysis Approach
* Key Insights Summary
* Detailed Insights
* Dashboard Overview
* Conclusion & Recommendations
* Tools & Technologies

---

## Case Study

This case study explores restaurant ratings in Mexico (2012) collected from real consumers. The dataset includes detailed information about restaurants, cuisines, consumer demographics, preferences, and multiple rating dimensions (overall, food, and service). The goal is to derive actionable insights by combining relational data modeling, exploratory data analysis, and interactive visualization.

---

## Dataset Overview

The dataset consists of multiple relational tables:

### Consumers

* **Consumer_ID** – Unique identifier
* **City, State, Country** – Location details
* **Latitude, Longitude** – Geographic coordinates
* **Smoker** – Smoking status
* **Drink_Level** – Abstemious / Casual / Social
* **Transportation_Method** – On foot / Public transport / Car
* **Marital_Status** – Single / Married
* **Children** – Dependent / Independent / Kids
* **Age** – Consumer age
* **Occupation** – Student / Employed / Unemployed
* **Budget** – Low / Medium / High

### Consumer_Preferences

* **Consumer_ID** – Unique identifier
* **Preferred_Cuisine** – Cuisine preferences

### Ratings

* **Consumer_ID** – Consumer identifier
* **Restaurant_ID** – Restaurant identifier
* **Overall_Rating** – 0 (Unsatisfactory), 1 (Satisfactory), 2 (Highly Satisfactory)
* **Food_Rating** – 0, 1, 2 scale
* **Service_Rating** – 0, 1, 2 scale

### Restaurants

* **Restaurant_ID** – Unique identifier
* **Name** – Restaurant name
* **City, State, Country** – Location
* **Zip_Code** – Postal code
* **Latitude, Longitude** – Geographic coordinates
* **Alcohol_Service** – None / Wine & Beer / Full Bar
* **Smoking_Allowed** – Smoking policy
* **Price** – Low / Medium / High
* **Franchise** – Franchise indicator
* **Area** – Open / Closed area
* **Parking** – None / Yes / Public / Valet

### Restaurant_Cuisines

* **Restaurant_ID** – Restaurant identifier
* **Cuisine** – Cuisine served

---

## Data Model (ER Diagram)

The dataset follows a relational structure connecting consumers, restaurants, cuisines, and ratings via primary and foreign keys. This design enables comprehensive analysis across demographics, preferences, and service attributes.

![Restaurant-ratings drawio](https://github.com/SnehaKaple/Restaurant-Ratings-Analysis/blob/main/ER-diagram.png)


---

## Data Preparation & Feature Engineering

### Data Import

* Imported all datasets using **folder ingestion** in Power BI.
* Transformed binary files and created individual tables for modeling.

### Calculated Fields (DAX)

**Age Group**

```
AgeGroup =
SWITCH(
    TRUE(),
    consumers[Age] <= 18, "Children and Adolescents",
    consumers[Age] <= 30, "Young Adults",
    consumers[Age] <= 45, "Adults",
    consumers[Age] <= 60, "Middle-aged Adults",
    "Seniors"
)
```

**Rating Categories**

```
Service_Rating_Category = SWITCH(TRUE(), ratings[Service_Rating] = 0, "Unsatisfactory", ratings[Service_Rating] = 1, "Satisfactory", "Highly Satisfactory")
Overall_Rating_Category = SWITCH(TRUE(), ratings[Overall_Rating] = 0, "Unsatisfactory", ratings[Overall_Rating] = 1, "Satisfactory", "Highly Satisfactory")
Food_Rating_Category    = SWITCH(TRUE(), ratings[Food_Rating] = 0, "Unsatisfactory", ratings[Food_Rating] = 1, "Satisfactory", "Highly Satisfactory")
```

These transformations improved interpretability and supported business-focused reporting.

---

## Analysis Approach

* Performed exploratory analysis across **location, demographics, and restaurant attributes**.
* Compared ratings across **price levels, parking availability, alcohol service, and franchise status**.
* Evaluated consumer behavior patterns related to **transportation, smoking, drinking habits, and budget**.
* Identified top-performing restaurants based on **food, service, and overall ratings**.

---

## Key Insights Summary

* Mexican cuisine is the most preferred across all consumer demographics.
* Young adults (under 30) represent the largest consumer segment in all states.
* Approximately **73% of restaurants are smoke-free**, aligning with majority consumer preferences.
* Public transportation is the dominant travel mode for dining (**61% of consumers**).
* Parking availability is more common among higher-priced restaurants.

---

## Detailed Insights

### Local & Demographic Insights

* San Luis Potosí has the highest concentration of consumers and restaurants.
* Smokers form a minority across all cities; Jiutepec reports a fully non-smoking consumer base.

### Dining & Hospitality Insights

* High-priced restaurants are more likely to offer parking and valet services.
* Most restaurants do not serve alcohol; only a small portion operate full bars.
* Non-franchise restaurants dominate the market and show balanced rating distributions.

### Behavioral Insights

* Students represent the majority occupation group, especially in San Luis Potosí and Tamaulipas.
* Budget levels are primarily medium among students and employed consumers.
* Drinking habits vary by state, with higher proportions of abstemious consumers in Morelos and Tamaulipas.

### Review-Based Insights

* **Top-performing restaurants** by overall satisfaction include Tortas Locas Hipocampo, Puesto de Tacos, and La Cantina Restaurante.
* Food and service ratings show consistency among top-ranked restaurants, indicating stable quality perception.

---

## Dashboard Overview

The Power BI dashboard provides:

* Interactive filters by city, state, and demographic attributes
* Rating comparisons across food, service, and overall satisfaction
* Visual analysis of cuisine popularity, parking availability, and alcohol service

## Dashboard
![Restaurant Ratings Analysis_page-0001](https://github.com/SnehaKaple/Restaurant-Ratings-Analysis/blob/main/Report-1.jpg)
![Restaurant Ratings Analysis_page-0002](https://github.com/SnehaKaple/Restaurant-Ratings-Analysis/blob/main/Report-2.jpg)
![Restaurant Ratings Analysis_page-0003](https://github.com/SnehaKaple/Restaurant-Ratings-Analysis/blob/main/Report-3.jpg)
![Restaurant Ratings Analysis_page-0004](https://github.com/SnehaKaple/Restaurant-Ratings-Analysis/blob/main/Report-4.jpg)
![Restaurant Ratings Analysis_page-0005](https://github.com/SnehaKaple/Restaurant-Ratings-Analysis/blob/main/Report-5.jpg)


---

## Conclusion & Recommendations

* Restaurants targeting young adults should focus on affordability and accessibility via public transport.
* Maintaining smoke-free environments aligns strongly with consumer expectations.
* Premium restaurants should ensure adequate parking facilities to support higher customer satisfaction.
* Mexican cuisine remains a strong and consistent market opportunity across regions.

---

## Tools & Technologies

* **Power BI** – Data modeling, DAX, interactive dashboards
* **Excel** – Initial data inspection
* **Relational Data Analysis** – Multi-table joins and ER modeling

---



