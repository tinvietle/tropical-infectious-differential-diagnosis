You are preparing ground truth for grading diagnostic lists. You are given one clinical case (`case_id`, `pmcid`, `case_text`) taken from a published case report. Settle the final diagnosis of the case from the paper, then write its MAIN DISEASE NAME.

## Step 1: find the final diagnosis (tools are REQUIRED)
- Try to open the paper: fetch https://pmc.ncbi.nlm.nih.gov/articles/<pmcid>/ . If that fails, fetch https://europepmc.org/article/PMC/<pmcid-number> , or use WebSearch with the case's most distinctive findings plus "case report" to find the paper.
- The `case_text` is the PRIMARY source: it describes the patient you are labeling. Decide which disease this patient has from the case text first (the text may already state or imply the diagnosis). The paper is SUPPORTING information: use it to confirm the diagnosis, to find the exact name the authors use, and to fill in what the text leaves out. Do not switch to a different disease only because the paper's title or headline topic is another disease (for example a paper about a complication, a drug reaction, an underlying condition or another patient in a series). If the case text is a fragment with no clear diagnosis, rely on the paper.
- Use the paper's title, abstract and discussion to settle the final diagnosis. Facts about this patient come from the case text or from the paper itself. Never claim to have read a source you did not open; if you could not open the paper, say so in `paper_opened` and rely on `case_text` and search results.
- Never use a differential diagnosis, a suspected or ruled-out diagnosis, or another patient's diagnosis. The main disease may differ from an infection named in the text if the paper's main diagnosis is something else (for example a background infection that is only a comorbidity).

## Step 2: write the main disease name
1. Name the primary disease only, as a short standard medical name of at most eight words. Leave out complications, secondary or accompanying conditions, triggers, the patient's setting (for example "in an immunocompromised patient" or "after transplantation"), and presentation details.
2. Keep the organism whenever the case text or the paper identifies it, as the usual short name of the disease: "pneumococcal meningitis", "Group B streptococcal meningitis", "Staphylococcus aureus bacteremia", "Salmonella osteomyelitis", "Legionella pneumonia", "Plasmodium vivax malaria", "tuberculous pericarditis", "cytomegalovirus colitis", "cryptococcal meningitis", "COVID-19 pneumonia". Keep the site when the disease is named by it: "abscess of liver", "herpes zoster ophthalmicus", "visceral leishmaniasis".
3. Use the generic syndrome name only when no organism is identified: "bacterial meningitis", "osteomyelitis", "infective endocarditis", "peritonitis", "urinary tract infection". Never invent an organism that is not stated.
4. If the paper names two equal diseases joined by "and" or "with", write the first and primary one; the second is a secondary condition.
5. Do not invent anything that is not in the paper or the case text. If there is no usable final diagnosis, write `unclear`.

## Output
Return ONLY valid JSON with exactly these keys, no markdown and no other text:
{"case_id": "<copied unchanged>",
 "final_diagnosis_note": "<one or two sentences: the paper's final diagnosis and the evidence for it>",
 "main_disease": "<the name>",
 "organism_defined": "yes" or "no",
 "paper_opened": true or false,
 "source_url": "<URL of the paper you used, or empty>"}
