# Problem Statement
Inefficient management of resources and staff can lead to loss of lives and revenue in a hospital. To solve this problem I have created a machine learning model to predict how long a patient is likely to stay at the hospital(in days) so as to combat this problem.

# Data
The link to the [dataset](https://drive.google.com/file/d/1AuAS7alsvVXZQIaqQyNunZT0vpEY9Y7L/view?usp=share_link) <br>
The data contains various information recorded during the time of admission of the patient. It only contains records of patients who were admitted to the hospital. The detailed data dictionary is given below:<br>
- patientid: Patient ID
- Age: Range of age of the patient
- gender: Gender of the patient
- Type of Admission: Trauma, emergency, or urgent
- Severity of Illness: Extreme, moderate, or minor
- health_conditions: Any previous health conditions suffered by the patient
- Insurance: Does the patient have health insurance or not?
- Admission_Deposit: The deposit paid by the patient during the admission
- Stay (in days): The number of days that the patient has stayed in the hospital. This is the target variable
- Available Extra Rooms in Hospital: The number of rooms available during the admission
- Department: The department which will be treating the patient
- Ward_Facility_Code: The code of the ward facility in which the patient will be admitted
- doctor_name: The doctor who will be treating the patient
- staff_available: The number of staff who are not occupied at the moment in the ward

# Result
I The model performed well with a Mean Absolute Error of 0.86 and R-Squared of 0.97<br>
You can check how I came up with the [model](https://github.com/KevKibe/Hospital-LOS-Prediction/blob/main/HospitalLOSpred.ipynb)

# Deployment
I deployed the model to [streamlit](https://kevkibe-hospital-los-prediction-main-0sls8c.streamlit.app/) and as a Flask API a REST API using Flask through Docker image to Google Cloud Run. <br>
You can use the [test data](https://github.com/KevKibe/Hospital-LOS-Prediction/blob/main/Test_data.xlsx) to see the output which is the same file with an additional column at the end with the predictions of the length of stay of each patient.

## Prerequisites
- Python3.7
- Docker
- 
## Installation
1. Clone the repository: `git clone https://github.com/KevKibe/Hospital-Patient-Length-of-Stay-Prediction`
2. Navigate to the project directory: `cd Hospital-Patient-Length-of-Stay-Prediction`
3. Install the dependencies: `pip install -r requirements.txt`

## Usage
1. Start the Flask API: `python main.py`
2. Access the web interface at: `https://claim-fraud-detection-f5m2fxxbbq-uc.a.run.app` or your local server `http://localhost:5000`
3. Run the model on test data: `python test.py`

## To deploy on an AWS EC2 instance
- Setup an EC2 instance and SSH to the instance.Use this as a [guide](https://www.machinelearningplus.com/deployment/deploy-ml-model-aws-ec2-instance/).
- Run  `git clone https://github.com/KevKibe/KevKibe/Hospital-Patient-Length-of-Stay-Prediction`
- Start up [Docker](https://docs.docker.com) and run `docker build -t dockerfile .`
- run `docker run -e PORT=8080 dockerfile`
- You can now get predictions from `http://<ec2-public-IP>:8080/predict`
