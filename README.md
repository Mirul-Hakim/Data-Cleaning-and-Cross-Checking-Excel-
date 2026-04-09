# Logistics Data Reconciliation & Claim Validation System
# Project Overview
This project addresses a critical data synchronization gap between a company's Headquarters (HQ) Operations system and the Accounting system.The discrepancy occurred because the Accounting system, which manages transport claims, was not receiving real-time updates from the Operations system due to IT integration delays. This resulted in legitimate transport claims being rejected as "records not found."
# Objective: 
To build an automated reconciliation engine in Excel to identify missing records, validate delivery statuses, and generate a standardized upload list for the IT department to sync the systems
# Technical Workflow
1. Data Integration & Transformation
- Consolidated multi-source data: HQ Legacy Data, HQ Current Data, and Accounting Ledger.
- Handled complex one-to-many relationships where a single Delivery Advice (DA) is linked to multiple Customer Advice (CA) entries.
2. Advanced Logic & Identification (The "Indicator" System)
- Status Versioning: Developed logic to interpret version suffixes (e.g., .1 for Active, .2 for Cancelled) to ensure only valid deliveries were processed.
- Custom Indicators: Created a unique "Indicator" key using IF and XLOOKUP to differentiate entries where CA numbers and quantities were identical, preventing false duplicate flags.3.
3. Data Cleaning (ETL)Performed rigorous data scrubbing to ensure 100% accuracy:
- Deduplication: Identified and removed redundant unique DA identifiers.
- Outlier Detection: Filtered inconsistent pricing or quantity entries.
- Validation: Verified DA authenticity against operational logs.
4. Automated Cross-Checking & Reporting
- Developed a Search System for rapid data retrieval and future auditing.
- Leveraged dynamic array functions (FILTER, SORTBY, LET) to generate a Missing Data Listing—a clean, ready-to-use dataset for the IT department to perform bulk system updates.
# Data Dictionary
1. Account Dataset
- Ref No(DO): Delivery Order number (Matches 'No DA' in HQ system).
- Invoice No: Official invoice reference for the claim.
- Exp Acc: Expense category (e.g., Prepayment).
- Net Price: Final payable amount after adjustments.
2. HQ Operational
- No DA: Delivery Advice (Primary Unique Key).
- No CA: Customer Advice (Sub-identifier; multiple CAs per DA).
- Version: Determines product status (Active vs. Cancelled).
- Indicator: Calculated Field: A custom unique key created to resolve many-to-many mapping conflicts.
- Delivery Name: Destination/Recipient location.
# Tools & Functions Used
1. Primary Tool: Microsoft Excel (Advanced)
2. Key Formulas:
- XLOOKUP / INDEX-MATCH / VLOOKUP for cross-system mapping.
- LET for optimized, readable formula structure.FILTER & SORTBY for dynamic reporting.
- IF, IFERROR & String Manipulation for Versioning logic.
3. Features: Power Query (ETL), Conditional Formatting (Error Highlighting), Data Validation.
# Impact & Business Value
1. Financial Integrity: Eliminated claim rejection errors by identifying 100% of the missing operational records.
2. Operational Efficiency: Automated a manual reconciliation process, reducing identification time significantly.
3. System Accuracy: Provided IT with a validated "Golden Record" for database correction, preventing future accounting discrepancies.
# Note on Data Privacy
- All datasets used in this repository have been anonymized and replaced with dummy data to protect company confidentiality while maintaining the integrity of the logic and technical demonstration.
# How to use
1. Open Logistics_Reconciliation_System.xlsx.
2. Input raw data into the HQ and Account tabs.
3. View the Cross-Check tab for immediate discrepancy results.
4. Export the Listing tab for IT system updates.
