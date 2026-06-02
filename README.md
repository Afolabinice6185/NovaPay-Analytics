# NovaPay-Analytics
The goal is to recommend optimizations that improve transaction success rates, enhance  user experience, balance regional growth, and mitigate operational risks.
# problem Statement
Analyze the provided transaction dataset (10,000 records from January 1 to June 28, 2024) 
to evaluate key performance indicators (KPIs), identify trends in volume and value, assess 
performance by channel, region, and transaction type, quantify success/failure rates, and 
deliver actionable insights.  
The goal is to recommend optimizations that improve transaction success rates, enhance 
user experience, balance regional growth, and mitigate operational risks. Present findings 
in a clear, professional format suitable for Product, Operations, and Risk stakeholders. 
Objectives 
• Calculate core KPIs (total volume, success rates, average transaction value). 
• Identify temporal trends and patterns. 
• Compare performance across transaction types, channels, and regions. 
• Highlight failure hotspots and improvement opportunities. 
• Provide 3–5 prioritized business recommendations. 
Deliverables Expected Executive summary, detailed EDA, visualizations with clear 
interpretations, and prioritized recommendations.

# Data Cleaning & Transformation Process (ETL)
To ensure data integrity and prepare the dataset for institutional-grade KPI reporting, a rigorous Extract, Transform, Load (ETL) pipeline was executed within Power Query and Power BI desktop. The process is broken down into four core phases:

# Phase 1: Data Hygiene & Error Rectification
-Removed Errors: Scanned all primary columns (TransactionID, CustomerID, and Amount) for technical anomalies, missing parameters, or formatting text mismatches. All corrupted rows were removed to ensure zero calculation distortion during aggregations.
-Removed Duplicates: Executed a system-wide duplicate removal using TransactionID as the unique identifier key. This eliminated double-counting risks, locking the final dataset down to verified, unique transactions.

# Phase 2: Time-Intelligence Engineering (Date Splitting)
To analyze temporal volatility and weekly success patterns, the raw Date column was parsed and expanded into dedicated time-intelligence fields
-Day Creation: Extracted day components to track intra-month payment behaviors.
-Week of Year Mapping: Engineered a Week index column, which directly enabled the creation of the weekly transaction volume trend visual.
-Month Extraction: Isolated calendar months to track high-level Month-over-Month (MoM) performance and volume distribution.

# Phase 3: Column Categorization & Grouping (Classification)
Amount Classification:Segmented the continuous raw financial value in the Amount column into structured logical tiers (e.g., Low, Medium, and High-Value tiers). This classification directly uncovered the reality that NovaPay operates primarily as a high-ticket commercial engine with a ₦249.62K average transaction value.

# Dax
 Created Measures to build dynamic, responsive visuals that update seamlessly across regional filters.

 # Primary Project Objective
To evaluate NovaPay’s 2024 transactional data across key regional hubs to uncover infrastructure vulnerabilities, isolate systemic transaction failures, and design a targeted optimization framework that recovers leaking transaction volume and maximizes platform profitability.

# The Dashboard Visualization
![<img width="510" height="286" alt="NovaPay screenshot" src="https://github.com/user-attachments/assets/7d404b25-b05a-434d-8f6c-b6938a64e95c" />
](NovaPay screenshot.png)
# breakdown Analysis of each Chat on the dashboard

1.
![<img width="510" height="323" alt="Week of the year" src="https://github.com/user-attachments/assets/73d607bc-fdf6-4121-b903-d3251eca8d98" />
](Week of the year.png)

# INSGHT
This line-and-area chart provides a critical view of NovaPay's operational stability over 26 weeks. It maps system transaction demand against platform processing efficiency.

-What the chart shows: The light blue filled area represents user transaction requests. It remains highly consistent, generally floating between 350 and 450 transaction attempts per week.

-The Problem: The dark blue line tracking the Success Rate does not match this steady user behavior. Instead, it experiences jagged, drastic drops—dipping down to 89% in Week 3, 90.2% in Week 11, and 90.2% in Week 20.

-The Insight: Because user demand is flat but performance drops vertically, the failures are not caused by an unexpected surge in customer traffic crashing your servers. Instead, these sharp drops point directly to external core-banking network switches or third-party payment gateways failing periodically.

# Recommendation and Take Away for Management
This visual proves that NovaPay's underlying infrastructure is unstable. The platform is losing processing fees and frustrating users during standard, predictable transaction weeks.
# To resolve this, 
Management should move away from generic software updates and approve automated multi-switch dynamic routing. When a partner switch drops (causing the sharp dips seen on the dark blue line), the system must instantly reroute transactions to a backup switch, smoothing out that volatile line and protecting your transaction volume.

2.
![<img width="508" height="360" alt="Volume and success rate NovaPay" src="https://github.com/user-attachments/assets/d8e3ce51-a5bb-471e-b241-a0f3ed539d8b" />
](Volume and success rate NovaPay.png)

# Key Insigt
-High Volume Concentration: All four major regional hubs (Port Harcourt, Abuja, Lagos, and Kano) show a high concentration of activity, each generating massive volumes around the 0.60bn to 0.64bn mark.

-Port Harcourt Leads: Port Harcourt holds the highest volume at 0.64bn, closely followed by Abuja at 0.63bn and Lagos at 0.62bn.

-Even Market Distribution: The volume variance between the highest performing region (Port Harcourt) and the lowest performing region (Kano, at 0.60bn) is remarkably narrow—only about 6.25%.

# Key Take Away
Instead of allocating resources based on regional ranking, management should treat Port Harcourt, Abuja, Lagos, and Kano as a unified, high-volume tier.

Actionable Strategy Elements
1. Implement Standardized InfrastructureAction: Deploy identical technology stacks and logistical frameworks across all four hubs.Reason: Uniform volume means a solution that fixes a bottleneck in Lagos will immediately scale to benefit Kano.

2. Standardize Procurement and CapacityAction: Negotiate bulk, centralized supply and vendor contracts for the 2.49bn total volume.Reason: Splitting procurement by region forfeits massive group-buying leverage

3. Audit Efficiency via the Success RateAction: Condition all future regional expansion budgets on the missing Success Rate metric.Reason: Volume is a vanity metric if failed deliveries or transactions are draining regional margins.

3
![<img width="510" height="372" alt="Failed Volume NovaPay" src="https://github.com/user-attachments/assets/5b2822ed-e915-436f-bfc4-34e7c60b19a9" />
](Failed Volume NovaPay.png)

This chart provides the missing operational context from your previous total volume data. It highlights Failed Volume by Region, Channel, and Transaction Type.While total transaction volume was evenly distributed across regions, your failure points are highly concentrated in specific channels and transaction types.

Key Insights
1. Abuja's USSD Channel is Severely CompromisedThe Issue: Abuja shows an alarming spike in failures within the USSD channel, specifically for Transfers (~6.5M) and Withdrawals (~7.4M).The Insight: This is the highest concentration of failed volume on the entire chart. It suggests a major network integration, telco partner, or core banking timeout issue specific to Abuja's USSD infrastructure.

2. Lagos Faces Massive Mobile App Transfer FailuresThe Issue: In Lagos, Mobile App Transfers (~7.0M) are drastically higher than any other failure type in that region.The Insight: Since Lagos is typically the tech-savvies market with high app adoption, this indicates either an app bug handling peak concurrency or severe infrastructure stress on the bank's processing switch during transfer routing.

3. Kano's Risk is Uniformly Spread Across Web and USSDThe Issue: Unlike Abuja and Lagos which have single massive pain points, Kano faces elevated failures across multiple fronts: Web Transfers (~6.6M) and USSD Withdrawals (~5.3M).

The Insight: This points toward a broader regional latency or platform-wide stability problem rather than a single isolated channel bug.

Strategic Recommendations for Management
Isolate and Fix Abuja USSD: Immediately task the engineering team to audit the USSD gateway routes in Abuja. Establish stronger SLAs with local telecommunication providers to handle timeouts.

Optimize Lagos App Transfer Switch: Deploy a dedicated load-balancer or optimize the payment gateway routing specifically for Mobile App Transfers originating from Lagos users to stop the 7M volume drain.

Audit Web Gateway APIs: Across both Kano and Abuja, Web Payments/Transfers hover consistently between 4M and 6M failures. Management should review the third-party payment gateways being utilized for web transactions, as they are underperforming compared to mobile apps.

# Summary 
Data reveals that while market demand (Total Volume) is perfectly balanced across Nigeria, operational execution (Failed Volume) is highly fragmented by region and technology channel.

# Conclusion
The project has achieved excellent market penetration with nearly equal, massive transaction volumes (~0.62bn per region) across Lagos, Abuja, Port Harcourt, and Kano. However, system instability is draining profitability. The business does not have a revenue generation problem; it has a revenue leakage problem caused by localized technical failures (primarily Abuja USSD and Lagos Mobile App).

# Actionable Recommendations
Standardize Commercial Scale: Treat all four regions as a single high-volume tier for infrastructure budget allocation.

Deploy Two Immediate Tech Fixes: Task engineering to fix the Abuja USSD gateway and optimize the Lagos Mobile App transfer switch to stop 14M+ combined transaction failures.

Enforce Success-Rate KPIs: Shift management tracking from "Total Volume" to "Net Successful Volume" to accurately measure regional profitability.
