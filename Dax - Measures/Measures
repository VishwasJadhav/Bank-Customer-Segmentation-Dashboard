# Total Revenue :

Total Revenue = SUM(Transactions[Transaction Amount])

---

# Average Transaction Value :

Avg Transaction Value = DIVIDE([Total Revenue], COUNT(Transactions[Transaction ID]))

---

# Retention Rate :

Retention Rate % = DIVIDE(
CALCULATE(COUNT('Customer Summary'[Customer ID]), 'Customer Summary'[RFM Segment] IN {
"Champions",
"Loyal Customers",
"Core Customers"} ), COUNT('Customer Summary'[Customer ID]) )

---

# Churn Risk % : 

Churn Risk % = COALESCE(
DIVIDE( CALCULATE(DISTINCTCOUNT('Customer Summary'[Customer ID]),
'Customer Summary'[RFM Segment] IN 
{"At Risk",
"Dormant Customers"}),
DISTINCTCOUNT('Customer Summary'[Customer ID]) ), 0)

---

# Credit Score : 

Weighted Score = (
'Customer Summary'[Balance Score] * 0.40 +
'Customer Summary'[Utilization Score] * 0.35 +
'Customer Summary'[Activity Score] * 0.10 +
'Customer Summary'[Age Score] * 0.15 )

Credit Score = 300 +('Customer Summary'[Weighted Score] * 6)

---

# Credit Category :

Credit Category = 
SWITCH( TRUE(),
'Customer Summary'[Credit Score] >= 740, "Excellent",
'Customer Summary'[Credit Score] >= 680, "Very Good",
'Customer Summary'[Credit Score] >= 620, "Good",
'Customer Summary'[Credit Score] >= 560, "Fair",
"Poor" )

# Risk Profile : 

Risk Profile = 
SWITCH(TRUE(),
-- LOW RISK
'Customer Summary'[Credit Score] >= 720,
"Low Risk",

-- HIGH RISK
'Customer Summary'[Credit Score] < 530,
"High Risk",

'Customer Summary'[RFM Segment] IN {
"At Risk",
"Dormant Customers"},
"High Risk",

-- MEDIUM RISK
"Medium Risk")

---

# RFM Score Logic : 

RFM Segment = 
SWITCH( TRUE(),
-- Champions
'Customer Summary'[R Score] >= 3 &&
'Customer Summary'[F Score] >= 3 &&
'Customer Summary'[M Score] >= 4,
"Champions",

-- Loyal Customers
'Customer Summary'[R Score] >= 3 &&
'Customer Summary'[F Score] >= 2 &&
'Customer Summary'[M Score] >= 3,
"Loyal Customers",

-- New Customers
'Customer Summary'[R Score] = 5 &&
'Customer Summary'[F Score] <= 2,
"New Customers",

-- At Risk
'Customer Summary'[R Score] <= 2 &&
'Customer Summary'[F Score] >= 3 &&
'Customer Summary'[M Score] >= 2,
"At Risk",

-- Dormant Customers
'Customer Summary'[R Score] <= 2 &&
'Customer Summary'[F Score] <= 2 &&
'Customer Summary'[M Score] <= 1,
"Dormant Customers",

-- Default Segment
"Core Customers" )

---

# Transaction Time Bucket :

Transaction Timeslot = SWITCH( TRUE(),
Transactions[Transaction Hour] < 6, "Night (12AM - 6AM)",
Transactions[Transaction Hour] < 10, "Early Morning (6AM - 10AM)",
Transactions[Transaction Hour] < 14, "Morning (10AM - 2PM)",
Transactions[Transaction Hour] < 18, "Afternoon (2PM - 6PM)",
Transactions[Transaction Hour] < 22, "Evening (6PM - 10PM)",
"Late Night (10PM - 12AM)" )

---

# Age Group : 

Age Group = SWITCH(TRUE(), 
'Customer Summary'[Age] < 18, "Under 18", 
'Customer Summary'[Age] <= 25, "18-25", 
'Customer Summary'[Age] <= 35, "26-35", 
'Customer Summary'[Age] <= 45, "36-45", 
"45-60")
