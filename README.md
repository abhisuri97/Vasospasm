# Vasospasm Predictor

Instructions:
- From Perioperative Data Warehouse, insert data into the `Data` subfolder
- Run Notebook 1 then Notebook 2 and lastly Notebook 3
- Notebook 3 may require a GPU to make training quicker. Google Colab is a great option. 

Structure of each Perioperative Data Warehouse file:

- flowsheets.csv:
    * Columns:  HSH_ADMSN_ID, FLO_MEAS_NAME, NORMALIZED_NAME, NFLO_MEAS_ID, GROUPED_FLO_ID, MEAS_VALUE, UNITS, RECODED_TIME
- flowsheets pressures.csv:
    * Columns: HSH_ADMSN_ID, FLO_MEAS_NAME, NORMALIZED_NAME, NFLOW_MEAS_ID, GROUPED_FLO_ID, MEAS_VALUE, UNITS, RECODED_TIME, SYSTOLIC, DIASTOLIC, MAP
- Labs.csv:
    * Columns:  HSH_ADMSN_ID, NORMALIZED_NAME, COMPONENT_ID, COMPONENT_NAME, ORD_VALUE, ORD_NUM_VALUE_CORRECTED, RESULT_TIME
- main.csv:
    * Columns: HSH_ADMSN_ID, ADMSN_MINUTES, ICU_MINS, DISCHARGE_MINUTES, IN_ICU_TIME, VERAPAMIL_TAKEN_TIME, BMI, AGE_LT90, SEX, ETHNICITY, RACE

Description of columns:
- HSH_ADMSN_ID: String with unique patient identifier
- FLO_MEAS_NAME: String with name of the flowsheet measure (from Epic)
- NORMALIZED_NAME: String with name of flowsheet measure that is standardized for groups of measures that should be averaged together
- NFLO_MEAS_ID: Integer ID uniquely identifying FLO_MEAS_NAME
- GROUPED_FLO_ID: Integer ID uniquely identifying NORMALIZED_NAME
- MEAS_VALUE: String raw value of output measure
- UNITS: String raw value of output units
- RECODED_TIME, RESULT_TIME: Time relative to ICU admission in minutes (integer)
- SYSTOLIC, DIASTOLIC: Integer for systolic and diastolic of pressure values
- ORD_VALUE: Value of lab
- ORD_VALUE_CORRECTED: Value of lab if there are any corrections that need to take place
- ADMSN_MINUTES: Integer time patient was admitted (should be 0)
- ICU_MINS: Integer time patient was admitted to ICU (relative to admission minutes)
- DISCHARGE_MINUTES: Integer time patient was discharged from ICU (relative to admission minutes)
- IN_ICU_TIME: Length of time patient was in ICU
- VERAPAMIL_TAKEN_TIME: Time (relative to admission) patient was administered verapamil. NaN/empty if not given
- BMI: BMI of patient (integer)
- AGE_LT90: 1 if patient is less than 90 years old, 0 otherwise.
- SEX: 'M' or 'F'
- ETHNICITY: String Ethnicity of patient
- RACE: String Race of patient