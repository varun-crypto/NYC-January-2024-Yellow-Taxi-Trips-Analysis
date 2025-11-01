# NYC January 2024 **Yellow Taxi** Trips Analysis

> **Note:** This analysis is **specifically for NYC Yellow Taxi trips** (January 2024), based on TLC Yellow Taxi data.

## 1. Project Background

**NYC Taxi Analytics** operates as a data-driven service analyzing taxi trip patterns in New York City. The company leverages official NYC Taxi & Limousine Commission (TLC) data to provide operational insights for:

- taxi fleet management  
- urban transportation planning  
- service optimization  

As a data analyst working with NYC transportation data, this project focuses on:

- understanding passenger behavior  
- identifying high-demand zones  
- analyzing revenue patterns  
- supporting strategic decision-making in urban mobility  

This analysis provides insights and recommendations on the following key areas:

- **Geographic Demand Patterns:** Identifying high-volume pickup and drop-off zones across NYC boroughs  
- **Temporal Travel Trends:** Analyzing peak hours and days of the week for taxi demand  
- **Passenger Behavior:** Understanding typical passenger counts and trip characteristics  
- **Revenue Analysis:** Examining fare structures, tipping patterns, and overall revenue generation  

- The Python code used to clean and transform the data for this analysis can be found **[here](#)**.
- The interactive Power BI dashboard used to explore trip patterns and revenue trends can be found **[here](#)**.

---

## 2. Data Structure & Initial Checks

The January 2024 NYC Yellow Taxi dataset consists of **one fact table** and **seven dimension tables**, with a total of **2.9 million trip records**.  
The data structure follows a **star schema** optimized for analytical queries.

### 2.1 Fact Table

**Yellow Taxi Trips Data**  
Contains trip-level transaction data, including:

- `trip_id`
- `datetime_id`
- `pickup_location_id`
- `dropoff_location_id`
- `passenger_count_id`
- `trip_distance_id`
- `rate_code_id`
- `payment_type_id`
- `fare_amount`
- extra charges
- taxes
- `tip_amount`
- tolls
- surcharges
- `total_amount`

### 2.2 Dimension Tables

- **Date Time Lookup:** datetime attributes (`datetime_id`, pickup/dropoff timestamps, hour, day, month, year, weekday)
- **Pickup Location Lookup:** geographic pickup data (`pickup_location_id`, `Borough`, `Zone`, `service_zone`)
- **Dropoff Location Lookup:** geographic dropoff data (`dropoff_location_id`, `Borough`, `Zone`, `service_zone`)
- **Passenger Count Lookup:** passenger count details (`passenger_count_id`, `passenger_count`)
- **Trip Distance Lookup:** trip distance info (`trip_distance_id`, `trip_distance`)
- **Rate Code Lookup:** rate type classifications (`rate_code_id`, `rate_code_name`, `RatecodeID`)
- **Payment Type Lookup:** payment method details (`payment_type_id`, `payment_type`, `payment_type_name`)

![Entity Relationship Diagram](Image 7)

---

## 3. Executive Summary

### 3.1 Overview of Findings

- **Total Revenue (Jan 2024):** **$77.5 million**  
- **Total Trips:** **2.9 million** Yellow Taxi trips  
- **Dominant Borough:** **Manhattan** (both pickups and drop-offs)  
- **Peak Demand:** Weekday afternoons (**4–6 PM**) and **mid-week (Wednesday)**  
- **Passenger Profile:** **Single-passenger trips = 86%** of all rides  
- **Average Fare:** **$26.40**  
- **Average Distance:** **3.8 miles**  

These metrics indicate **stable, commuter-driven Yellow Taxi operations** suitable for:

- fleet optimization  
- demand forecasting  
- targeted pricing and driver scheduling  

![NYC January 2024 Dashboard](Image 6)

---

## 4. Insights Deep Dive

### 4.1 Geographic Demand Patterns

1. **Manhattan Highest Volume**  
   - Manhattan shows the **highest concentration** of both pickups and drop-offs.  
   - Certain zones recorded **150,000+ trips** in January 2024.  
   - This represents **~65–70%** of all Yellow Taxi activity in NYC → Manhattan remains the **economic and transportation hub**.

2. **JFK Airport as Secondary Hotspot**  
   - JFK Airport zone shows the **second-highest pickup concentration**.  
   - Indicates **strong airport-to-city demand** → scope for **airport-focused services** and **peak-time surge pricing**.

3. **Outer Boroughs Lower Activity**  
   - Queens, Brooklyn, and the Bronx show **much lighter Yellow Taxi usage**, most zones **<10,000 trips**.  
   - Either an **opportunity for expansion** or **evidence of preference for alternative transport (subway, Uber, local services)**.

4. **Pickup vs Drop-off Symmetry**  
   - Heat maps for pickup and drop-off are **nearly identical**.  
   - Suggests most rides are **point-to-point within Manhattan**, not cross-borough.  
   - **Fleet positioning** should prioritize **Manhattan coverage**, with **limited vehicles** in outer boroughs.

![Total Trips by Pickup and Dropoff Zone](Image 2)

---

### 4.2 Temporal Travel Trends (By Hour of Day)

1. **Peak Hours: 16:00–18:00 (4–6 PM)**  
   - Over **200,000 trips** in this 2-hour window.  
   - ~**14% of daily volume** → **commuter-driven** demand.

2. **Low Activity: 0:00–6:00 AM**  
   - Trips drop **<80,000 per hour**.  
   - **5:00 AM** is the **lowest** point → **minimum fleet requirement** period.

3. **Daytime Build-Up (7:00–23:00)**  
   - Gradual increase from 7:00 AM  
   - **11:00 AM–11:00 PM** → consistently **>130,000 trips/hour**  
   - Indicates **broad daytime utilization**.

4. **Evening Demand (19:00–23:00)**  
   - Still **150,000–180,000 trips/hour**  
   - Likely **dining, entertainment, tourism** usage.

![Total Trips by Pickup Hour](Image 3)

---

### 4.3 Day-of-Week Patterns

1. **Wednesday = Peak Day**  
   - ~**490,000 trips**  
   - Followed closely by **Tuesday** and **Thursday** (~480,000–485,000)  
   - Indicates **business/commercial travel** as a key driver.

2. **Weekend Dip**  
   - **Sunday** lowest: ~**380,000 trips** (≈ **22% lower than Wednesday**)  
   - **Saturday** slightly higher than Sunday, but still **below weekdays**.

3. **Monday Ramp-Up**  
   - ~**410,000 trips** → gradual start of workweek.

4. **Stable Mid-Week Window**  
   - Tue–Thu all within **2%** of each other → **predictable demand** → good for **driver scheduling** and **shift incentives**.

![Total Trips by Day](Image 4)

---

### 4.4 Passenger Behavior

1. **Single-Passenger Dominance**  
   - ~**2.5 million trips** → **86%** of all Yellow Taxi rides.  
   - Confirms taxis are used **primarily for individual travel**.

2. **Two-Passenger Trips**  
   - Drop to ~**350,000 trips** → **12%** of total.

3. **4+ Passenger Trips Are Rare**  
   - Each category **<50,000 trips**  
   - 5–9 passengers combined **<2%** of total  
   - Implies **low demand** for large-capacity vehicles.

4. **Implication**  
   - Passenger distribution follows an **exponential decay**.  
   - Any **pooled / shared / carpooling** initiative would need **strong incentives** to change behavior.

![Total Trips by Passenger Count](Image 5)

---

## 5. Recommendations (for Yellow Taxi Operations)

1. **Geographic Focus on Manhattan**  
   - Since **65–70%** of trips are in Manhattan, **prioritize driver availability** there.  
   - **Reduce fleet presence** in outer boroughs during off-peak to cut idle time.

2. **Peak-Hour Optimization (16:00–18:00)**  
   - Apply **dynamic pricing** and **driver bonuses**.  
   - **Deploy +15–20% vehicles** in this 2-hour window to:
     - capture demand  
     - reduce wait times  
     - maximize revenue

3. **Mid-Week Capacity Planning**  
   - Increase fleet on **Tue, Wed, Thu** (480k–490k trips/day).  
   - Offer **shift premiums** to ensure service levels.

4. **Fleet Composition: Single-Passenger First**  
   - Since **86%** rides are 1 passenger → favor **sedans**, **hybrids**, **EVs**.  
   - Larger vehicles only for **airport** or **group-trip** corridors.

5. **Weekend Strategy**  
   - With **Sunday 22% lower** than Wednesday:
     - lower baseline fleet  
     - offer **weekend promotions** or **loyalty boosts**  
     - target **tourist corridors** and **airport flows**

---

## 6. Assumptions and Caveats

To handle data quality and operational edge cases, the following assumptions were applied:

1. **Passenger Count Fix**
   - Trips with **0 passengers** were recoded to **1 passenger**  
   - Rationale: likely **data entry error**, not an actual empty paid trip  
   - Affected **~0.5–1%** of records

2. **Timestamp Order Correction**
   - If **pickup time > dropoff time**, timestamps were **swapped**  
   - Rationale: sequence entry error  
   - Ensures valid **trip duration** metrics

3. **Extreme Duration Filter**
   - Trips **>24 hours** were **excluded**  
   - Rationale: likely errors / nonstandard events  
   - Affected **<0.1%** of trips

4. **Fare–Distance Imputation**
   - For **0 distance but positive fare** → distance estimated as:  
     \[
     \text{distance} = \frac{\text{fare\_amount} - 2.5}{2.5}
     \]
     based on NYC Yellow Taxi base and per-mile structure.
   - For **distance but 0 fare** → fare estimated as:  
     \[
     \text{fare} = 2.5 + ( \text{trip\_distance} \times 2.5 )
     \]

5. **Negative Monetary Values**
   - Trips with **all negative** amounts (fare, taxes, surcharges) were **converted to positive**  
   - Rationale: treat as **accounting sign errors** / refunds that should be **positive for analysis**

6. **Unknown / Erroneous Zones**
   - **Location IDs 264 and 265** were **excluded**  
   - Rationale: not part of official TLC taxi zones

---




