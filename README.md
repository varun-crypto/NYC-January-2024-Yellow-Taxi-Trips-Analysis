# NYC January 2024 Yellow Taxi Trips Analysis

> **Note:** This analysis is **specifically for Yellow Taxi** trips.


## The goal of this project is to analyze January 2024 NYC yellow taxi trip data to identify trends in revenue, trip volumes, and passenger behavior patterns. Using Power BI for interactive visualization and Python for data transformation, this analysis provides actionable insights into peak travel times, high-demand geographic zones, and revenue optimization opportunities to support strategic decision-making in urban taxi operations.


## Project Background

NYC Taxi Analytics operates as a data-driven service analyzing taxi trip patterns in New York City. The company leverages official NYC Taxi & Limousine Commission (TLC) data to provide operational insights for taxi fleet management, urban transportation planning, and service optimization. As a data analyst working with NYC transportation data, this project focuses on understanding passenger behavior, identifying high-demand zones, and analyzing revenue patterns to support strategic decision-making in urban mobility.

This analysis provides insights and recommendations on the following key areas:

- **Geographic Demand Patterns:** Identifying high-volume pickup and drop-off zones across NYC boroughs
- **Temporal Travel Trends:** Analyzing peak hours and days of the week for taxi demand
- **Passenger Behavior:** Understanding typical passenger counts and trip characteristics
- **Revenue Analysis:** Examining fare structures, tipping patterns, and overall revenue generation

The Python code used to clean and transform the data for this analysis can be found here.  
The interactive Power BI dashboard used to explore trip patterns and revenue trends can be found here.

## Data Structure & Initial Checks

The NYC taxi trip database consists of one fact table and seven dimension tables, with a total of 2.9 million trip records for January 2024. The data structure follows a star schema optimized for analytical queries. A description of each table is as follows:

### Fact Table

**Yellow Taxi Trips Data:** Contains trip-level transaction data including trip_id, datetime_id, pickup_location_id, dropoff_location_id, passenger_count_id, trip_distance_id, rate_code_id, payment_type_id, fare_amount, extra charges, taxes, tip_amount, tolls, surcharges, and total_amount

### Dimension Tables

- **Data Time Lookup:** Contains datetime attributes (datetime_id, pickup/dropoff timestamps, hour, day, month, year, weekday)
- **Pickup Location Lookup:** Geographic pickup data (pickup_location_id, Borough, Zone, service_zone)
- **Dropoff Location Lookup:** Geographic dropoff data (dropoff_location_id, Borough, Zone, service_zone)
- **Passenger Count Lookup:** Passenger count details (passenger_count_id, passenger_count)
- **Trip Distance Lookup:** Trip distance information (trip_distance_id, trip_distance)
- **Rate Code Lookup:** Rate type classifications (rate_code_id, rate_code_name, RatecodeID)
- **Payment Type Lookup:** Payment method details (payment_type_id, payment_type, payment_type_name)

![Entity Relationship Diagram](Image 7)

## Executive Summary

### Overview of Findings

January 2024 NYC yellow taxi operations generated $77.5 million in revenue across 2.9 million trips, with Manhattan dominating both pickup and drop-off activity. Peak demand occurs during weekday afternoons (4-6 PM) and mid-week (Wednesday), indicating strong commuter-driven usage patterns. The overwhelming prevalence of single-passenger trips (86%) highlights individual travel as the primary use case, while the consistent $26.40 average fare and 3.8-mile average distance suggest stable operational metrics ideal for fleet optimization and demand forecasting.

![NYC January 2024 Dashboard](Image 6)

## Insights Deep Dive

### Geographic Demand Patterns:

**Main insight 1:** Manhattan experiences the highest concentration of both pickups and drop-offs, with certain zones showing 150,000+ trips during January 2024. This represents approximately 65-70% of all taxi activity in NYC, establishing Manhattan as the economic and transportation hub.

**Main insight 2:** JFK Airport zone shows the second-highest trip concentration on the pickup map, indicating significant airport-to-city travel demand. This presents opportunities for specialized airport service offerings and surge pricing strategies during peak travel times.

**Main insight 3:** The geographic distribution reveals that outer boroughs (Queens, Brooklyn, Bronx) show significantly lighter taxi activity, with most zones registering below 10,000 trips. This suggests potential market expansion opportunities or indicates customer preference for alternative transportation in these areas.

**Main insight 4:** Pickup and drop-off heat maps show nearly identical patterns, suggesting most trips are point-to-point within Manhattan rather than cross-borough travel. This indicates fleet positioning strategies should focus on Manhattan coverage with limited vehicles stationed in outer boroughs.

![Total Trips by Pickup and Dropoff Zone](Image 2)

### Temporal Travel Trends:

**Main insight 1:** Taxi demand peaks between 16:00 and 18:00 (4-6 PM) with over 200,000 trips, coinciding with traditional office closing hours. This 2-hour window represents approximately 14% of daily trip volume, indicating strong commuter-driven demand patterns.

**Main insight 2:** Early morning hours (0:00-6:00) show significantly reduced activity, with trip counts dropping below 80,000 per hour. The lowest point occurs around 5:00 AM, representing the minimum fleet requirement period for cost optimization.

**Main insight 3:** Trip volume shows a gradual increase starting at 7:00 AM through the afternoon, with relatively stable high demand from 11:00 AM to 11:00 PM. This 12-hour window maintains consistent utilization above 130,000 trips per hour.

**Main insight 4:** The late-evening period (19:00-23:00) maintains moderately high demand around 150,000-180,000 trips per hour, suggesting entertainment and dining-related travel extends the peak demand window beyond traditional commute hours.

![Total Trips by Pickup Hour](Image 3)

### Day-of-Week Patterns:

**Main insight 1:** Wednesday records the highest trip volume at approximately 490,000 trips, followed closely by Tuesday and Thursday, each with around 480,000-485,000 trips. This mid-week peak suggests business travel and commuting patterns drive maximum demand.

**Main insight 2:** Weekend days show a noticeable decline, with Sunday recording the lowest trip count at approximately 380,000 trips (22% lower than Wednesday). Saturday shows slightly higher activity than Sunday but remains well below weekday levels.

**Main insight 3:** Monday shows moderate activity at approximately 410,000 trips, suggesting a gradual ramp-up as the work week begins. Friday experiences a slight decline from mid-week peaks at around 430,000 trips, possibly due to flexible work arrangements or early weekend departures.

**Main insight 4:** The relatively consistent high demand Tuesday through Thursday (all within 2% of each other) indicates stable business travel patterns and presents opportunities for predictable fleet deployment and driver scheduling during these days.

![Total Trips by Day](Image 4)

### Passenger Behavior:

**Main insight 1:** Single-passenger trips dominate with approximately 2.5 million trips (86% of total volume), demonstrating that taxis serve primarily individual travelers rather than groups. This finding has significant implications for vehicle type selection and ride-sharing program viability.

**Main insight 2:** Two-passenger trips show a dramatic drop to approximately 350,000 trips, representing only 12% of total volume. This steep decline continues with three or more passengers, suggesting group travel is a minority use case.

**Main insight 3:** Trips with 4+ passengers become increasingly rare, with counts dropping below 50,000 for each category. Trips with 5-9 passengers collectively represent less than 2% of total trips, indicating minimal demand for larger vehicle capacity.

**Main insight 4:** The exponential decay curve in passenger distribution suggests that any shared-ride or carpooling initiatives would require strong incentives or awareness campaigns to modify customer behavior, as current usage patterns heavily favor individual travel.

![Total Trips by Passenger Count](Image 5)

## Recommendations:

Based on the insights and findings above, we recommend the NYC Taxi Operations and Fleet Management team to consider the following:

1. **Geographic Focus:** With 65-70% of trips concentrated in Manhattan, prioritize fleet positioning and driver availability in Manhattan zones during operational hours. Consider reducing fleet presence in outer boroughs during off-peak hours to improve vehicle utilization rates and reduce idle time.

2. **Peak Hour Optimization:** Implement dynamic pricing and driver incentives during the 16:00-18:00 peak window to maximize revenue potential. Deploy 15-20% additional vehicles during this 2-hour period to capture high-demand opportunities and reduce customer wait times.

3. **Mid-Week Capacity Planning:** Increase driver scheduling and fleet availability on Tuesday, Wednesday, and Thursday when demand is highest (480,000-490,000 trips per day). Offer shift premiums during these days to ensure adequate driver availability and service levels.

4. **Single-Passenger Vehicle Efficiency:** Given 86% of trips involve single passengers, optimize fleet composition toward standard sedans rather than larger vehicles. Consider testing smaller, fuel-efficient vehicles or electric vehicles to reduce operational costs while meeting the predominant single-passenger use case.

5. **Weekend Strategy Adjustment:** With Sunday trips 22% lower than Wednesday, implement reduced fleet deployment and alternative pricing strategies on weekends. Consider offering promotional rates or loyalty program bonuses to stimulate weekend demand and improve vehicle utilization during traditionally slower periods.

## Assumptions and Caveats:

Throughout the analysis, multiple assumptions were made to manage challenges with the data. These assumptions and caveats are noted below:

**Assumption 1:** Trips with zero passenger count were recoded to one passenger, assuming data entry errors rather than genuine empty taxi trips. This affected approximately 0.5-1% of records and ensures realistic passenger count analysis.

**Assumption 2:** When pickup time occurred after drop-off time, the timestamps were swapped, assuming data entry sequence errors. This logical correction was applied to maintain data integrity for trip duration calculations.

**Assumption 3:** Trips lasting longer than 24 hours were excluded from the analysis as outliers, assuming they represent data errors or unusual circumstances not representative of typical taxi operations. This affected less than 0.1% of trips.

**Assumption 4:** For trips with zero distance but positive fare amount, distance was calculated using the formula (fare_amount - 2.5) / 2.5, based on NYC taxi rate structure. Similarly, for trips with distance but zero fare, fare was estimated using 2.5 + (trip_distance * 2.5).

**Assumption 5:** Trips with all negative monetary values (fare, taxes, surcharges) were converted to positive values, assuming accounting system errors or refund entries that should be represented as positive transactions for analysis purposes.

**Assumption 6:** Location IDs 264 and 265 were excluded from analysis as they represent unknown or erroneous zones not part of the official TLC taxi zone system.


