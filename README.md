Supplementary Methods for:
"Performance of Local Large Language Models for Adjudicating Heart Failure Hospitalizations"

This repository contains adjudication criteria and prompting strategies used in the study.

Last updated: April 2026

Supplement

Heart Failure Hospitalization Adjudication Criteria
Guidance for Adjudicating Heart Failure Hospitalizations
Purpose
Determine whether new or worsening heart failure (HF) was a reason for the hospitalization, regardless of whether it was the primary reason, using your expert judgment and only the discharge summary. The core question is: Was heart failure an active problem requiring hospital-level management during this admission?

How to Adjudicate
 Label as “HF Hospitalization: YES” if:
•	In your judgment, HF was a reason for the admission.
•	The discharge summary indicates decompensated HF, volume overload, or HF exacerbation requiring hospital-level treatment.
•	If volume overload, it should be at least partially attributable to heart failure (not solely due to cirrhosis, nephrotic syndrome, or end-stage renal disease without HF contribution).
Common phrases you may see:
•	“Admitted for acute decompensated heart failure.”
•	“Presented with worsening dyspnea due to CHF.”
•	“Volume overload requiring IV diuresis.”
•	“Acute systolic/diastolic heart failure exacerbation.”

Examples of hospital-level treatment that support labeling as YES:
•	IV diuretics (e.g., IV furosemide, bumetanide).
•	Significant escalation from home diuretic regimen.
•	Inotropic therapy or other interventions for HF exacerbation.

Label as “HF Hospitalization: NO” if:
•	The patient was admitted for another reason, and HF was not a reason for admission, even if HF is listed on the problem list.
•	HF was stable or incidental during the hospitalization and did not contribute to the need for admission.
•	The discharge summary lacks sufficient clarity to determine whether HF was a reason for admission.
•	The reason for volume overload was cardiac surgery. 

Examples:
•	“Admitted for elective hip replacement. History of stable HFrEF.”
•	“Admitted for elective TAVR or CABG; HF listed but stable.”
•	“Sepsis admission; volume overload noted but attributed solely to ESRD.”

 
Prompting Strategies

Structured:
You are an expert cardiologist reviewing a patient's discharge summary. Your task is to extract specific information about heart failure.
This means the patient was admitted because of new or worsening heart failure symptoms, or because of a significant HF-related issue that required active inpatient management.
To classify the case as “HF Hospitalization: Yes”, there should be clear evidence of all the following:
- Symptoms consistent with HF — such as dyspnea, orthopnea, PND, or peripheral edema at the time of admission, AND
- A clinical assessment attributing those symptoms to HF (e.g., “admitted for acute decompensated HF” or “CHF exacerbation”), AND
- Active treatment for HF during hospitalization — such as IV diuretics, inotropes, or escalation of chronic HF medications.

Do NOT classify as “HF Hospitalization: Yes” if:
- HF is only mentioned in the past medical history,
- HF is not discussed in the hospital course or discharge assessment,
- The patient was admitted for another reason (e.g., infection, cirrhosis, renal failure) and volume overload is likely from non-cardiac causes,
- There is no indication of new or worsening HF, or no specific HF-directed therapy was given,
- Patient had post cardiac surgery volume overload but was not admitted specifically for heart failure. 

Use “HF Hospitalization: Yes” only when:
The discharge summary provides enough evidence that HF was an active reason for the hospitalization and required management.
Base your judgment on the content of the discharge summary alone, using your clinical expertise.
Even if heart failure is not mentioned or is explicitly ruled out, you MUST still provide a complete JSON object with all specified keys.
Your output MUST be a single, valid JSON object with the following keys:
- "hf_is_admission_reason": A string, must be either "Yes" or "No".
--- DISCHARGE SUMMARY ---
{discharge_summary}
--- END SUMMARY ---

The output must be ONLY the valid JSON object and nothing else.
JSON Output:"""

Direct:

Read the following discharge summary and determine if heart failure was a reason for the hospitalization. Answer with only 'Yes' or 'No'.

Role:

You are a board-certified cardiologist and clinical trial endpoint adjudicator tasked with adjudicating heart failure trial endpoints.
Read the following discharge summary and determine if heart failure was a reason for the hospitalization. Answer with only 'Yes' or 'No'.


