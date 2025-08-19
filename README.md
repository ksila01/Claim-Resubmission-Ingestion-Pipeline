# Insurance Claim Resubmission Eligibility
***



![](./images/image.png)








***
## Project Overview

This project focuses on normalizing insurance claim data from multiple sources (CSV and JSON formats), assessing eligibility for resubmission based on predefined business rules, and generating a list of resubmission candidates. The goal is to improve the claims review process by identifying claims that are eligible for resubmission with suggested changes.

***

**Steps Involved:**

I.  **Data Normalization:**
* The project processes insurance claim data from two sources:
  1. CSV (emr_alpha.csv): Contains claims in CSV format.
  2. JSON (emr_beta.json): Contains claims in JSON format.
Both sources are normalized to a common schema for consistency and further processing.

II. **Resubmission Eligibility:**

* Claims are checked for resubmission eligibility based on the following criteria:

a. Status: Must be "denied".

b. Patient ID: Must not be null.

c. Submission Date: Must be more than 7 days old.

d. Denial Reason: Must be classified as retryable (either from a predefined list or inferred from ambiguous reasons).

III. **Output Generation:**

A list of eligible claims for resubmission is generated, containing:

a. Claim ID
b. Resubmission Reason
c. Recommended Changes

IV. **Metrics and Logging:**

The process logs the number of claims processed, the number of claims from each source, the number of claims flagged for resubmission, and the number excluded with reasons.

V. **Evaluation**
* Data Processing and Normalization:
* The project involves processing insurance claims from two data formats:
* CSV Data (emr_alpha.csv): Processed into a standardized format containing details such as claim_id, patient_id, procedure_code, denial_reason, submitted_at, and status.
* JSON Data (emr_beta.json): Similar structure as the CSV data but coming from a different source with slight variations in field names and structure.
* The normalization process ensures that both datasets are transformed into a consistent format for further analysis.

VI. **Eligibility Logic:**

* The resubmission eligibility is determined by:

* Claim Status: Claims that are not denied are excluded.

* Patient ID: Claims with a missing patient_id are excluded.

* Submission Date: Claims submitted within the last 7 days are excluded.

* Denial Reason: Claims are checked against a list of retryable denial reasons. Ambiguous reasons (e.g., "incorrect procedure") are inferred as retryable.

VII. **Resubmission Candidates:**

* The eligible claims for resubmission are flagged with detailed suggestions on how to fix the issues (e.g., correcting the NPI number or prior authorization). This helps automate the resubmission process and ensure quicker resolutions.

**Output:**

The final output is stored in a file called resubmission_candidates.json, containing the list of eligible claims for resubmission.

![](./images/Capture.png)


VIII. **Conclusions and Recommendations**

* Based on the analysis and models developed, here are the conclusions and recommendations:

* Claim Data Normalization: The process of normalizing claims from different sources (CSV and JSON) ensures data consistency, which is critical for the subsequent analysis and resubmission decisions.

* Eligibility for Resubmission: The eligibility criteria effectively identify claims that can be resubmitted. Claims with ambiguous denial reasons are handled through inference, making the logic adaptable to different denial scenarios.

* Automation Potential: This system can be further integrated into an automated claims processing pipeline to reduce manual review. The suggested changes in the resubmission output can guide claim adjusters in correcting and resubmitting claims more efficiently.

* Monitoring and Continuous Improvement: Continuous tracking of claims flagged for resubmission and their resolution rates can help improve the accuracy of the eligibility checks over time. Monitoring metrics such as resubmission success rates can drive improvements in the logic used for determining eligibility.

**Requirements**

*Python 3.7+
* Libraries
* pandas
* datetime
* json
* logging
