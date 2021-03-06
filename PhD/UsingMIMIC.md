# There will be three dataset we want to use.

1. MIMIC-ED
2. MIMIC-IV
3. MIMIC-CXR (for this dataset
   we want to use the one with JPG only)

# MIMIC-ED

- MIMIC-ED is usable as a standalone research database
  but may also be linked to MIMIC-IV and MIMIC-CXR [1,3]
- MIMIC-ED is composed of a single patient tracking table
  edstays, and five data tables: diagnosis, medrecon, pyxis, triage, and vitalsig.

## edstays

Patient stays are tracked in the edstays table.

- subject_id
  The `subject_id` value provides an implicit link between the datasets; that is all three databases refer to the same individual with the same `subject_id`.
- hadm_id
  can be linked with the hadm_id in MIMIC-IV to obtain further detail about the patient’s hospital stay.
- stay_id
  All ED stays in MIMIC-ED, represented by `stay_id`, are present in the MIMIC-IV transfers table.
- intime
- outtime

## **diagnosis**

provides coded diagnoses for the patient in the International Classification of Diseases (ICD) Ninth or Tenth revision (ICD-9 or ICD-10).

- subject_id
- stay_id
- seq_num

- icd_code (**Code representation of the diagnosis**, icd => International Classification of Diseases)
- icd_version
- icd_title (textual description of the icd code)

## medrecon

provides medicine reconciliation for each patient, that is a list of the medications which the patient was taking prior to their ED stay.

- subject_id
- stay_id
- charttime (date and time at which the medicine reconciliation was documented)
- name
- gsn (provides the Generic Sequence Number)
- ndc (National Drug Code)
- etc_rn (sequential monotonically increasing integer)(etc => ontology for grouping together drugs of a similar class)
- etccode (coded form of the ontology group)
- etcdescription (textual description of the ontology group)

## pyxis

The pyxis table provides dispensation information for medications.

- subject_id
- stay_id
- charttime (time at which the medication was dispensed)
- med_rn (delineates these medications)
- name (textual description of the medication dispensed)
- gsn_rn (delineates multiple GSN values associated with the same medication. Note that a gsn of 0 indicates that the GSN is missing.)
- gsn (Generic Sequence Number)

## **triage** (! important)

Provide information collected from the patient at the time of triage.All patients who present to the ED are immediately triaged, a process which involves assessing their health status and ascertaining the reason for their visit

- subject_id
- stay_id
- temperature
- heartrate
- resprate (respiratory rate)
- o2sat (oxygen saturation)
- sbp (systolic blood pressure)
- dbp (diastolic blood pressure)
- pain (Patient reported pain level)
- acuity (the care provider will assign an integer level of severity (acuity), where 1 indicates the highest severity and 5 indicates the lowest severity.)
- chiefcomplaint (free-text field which contains the patient’s reported reason for presenting to the ED)

# MIMIC-IV

It has three different folders, including core, hosp, and icu.

## Core
The core module stores patient tracking information necessary for any data analysis using MIMIC-IV. The core module contains three tables: **patients, admissions, and transfers**. These tables provide **demographics** for the patient, a record for each hospitalization, and a record for each ward stay within a hospitalization.

### Admissions table.

#### admittime, dischtime, deathtime
`admittime` provides the date and time the patient was admitted to the hospital, while `dischtime` provides the date and time the patient was discharged from the hospital. If applicable, `deathtime` provides the time of in-hospital death for the patient. 

#### admission_type
`admission_type` is useful for classifying the urgency of the admission. There are 9 possibilities: `AMBULATORY OBSERVATION`, `DIRECT EMER.`, `DIRECT OBSERVATION`, `ELECTIVE`, `EU OBSERVATION`, `EW EMER.`, `OBSERVATION ADMIT`, `SURGICAL SAME DAY ADMISSION`, `URGENT`.

#### admission_location, discharge_location
`admission_location` provides information about the location of the patient prior to arriving at the hospital. Similarly, `discharge_location` is the disposition of the patient after they are discharged from the hospital.

#### **insurance, language, marital_status, ethnicity**
Information about patient demographics for the given hospitalization.

#### edregtime, edouttime
The date and time at which the patient was registered and discharged from the emergency department.

#### hospital_expire_flag
This is a binary flag which indicates whether the patient died within the given hospitalization. 1 indicates death in the hospital, and 0 indicates survival to hospital discharge.

### Patients

## Hosp
The hosp module contains data derived from the hospital wide EHR.

## ICU
The icu module contains data sourced from the clinical information system at the BIDMC: MetaVision (iMDSoft). MetaVision tables were denormalized to create a star schema where the icustays and d_items tables link to a set of data tables all suffixed with "events".

