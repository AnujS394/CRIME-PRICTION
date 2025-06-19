# 🕵️ Crime Pattern Detection Using Python

This project analyzes crime records using **Python** to uncover patterns across time and location.  
By transforming and visualizing features such as hour of occurrence, crime type, and police area, the project uncovers when and where crimes most frequently occur.

---

## 📌 Dataset Overview

The notebook uses a **simulated crime dataset** with fields like:

- `DATE OCC`: Date when the crime occurred
- `TIME OCC`: Time of crime (in military time)
- `AREA NAME`: Division (e.g., Central, Hollywood)
- `Crm Cd Desc`: Crime description

---

## 🚀 Key Features

| Task                        | Description |
|-----------------------------|-------------|
| 🧹 Data Preprocessing        | Extract hour from military time, encode labels |
| 📊 Frequency Analysis        | Top crimes and their frequency |
| 🕐 Hourly Distribution       | Crimes by time of day |
| 📍 Area Analysis             | Crimes by LAPD division |
| 🤖 Classification Model     | Random Forest Classifier for crime prediction |
| 📈 Evaluation Metrics        | Accuracy, Confusion Matrix, Classification Report |

---

## 🧪 Technologies Used

- `pandas`, `numpy` – data manipulation  
- `matplotlib`, `seaborn` – plotting  
- `sklearn` – machine learning and evaluation  
- `LabelEncoder`, `RandomForestClassifier`  

---

## 📸 Sample Outputs

![Screenshot 2025-06-19 200559](https://github.com/user-attachments/assets/20957a00-7fda-4822-a663-5a329230b54f)
![Screenshot 2025-06-19 200535](https://github.com/user-attachments/assets/eb7a4c80-e14f-48df-8698-5ceb3078272f)
![Screenshot 2025-06-19 200512](https://github.com/user-attachments/assets/c9042a34-7afc-4c6f-a33f-9c46270a15b3)

### 🔹 Top Crime Types (Bar Chart)
Shows the most frequent offenses like:
- Assault with Deadly Weapon
- Burglary
- Vehicle Theft

### 🔹 Hourly Crime Distribution
A countplot shows when crimes peak throughout the day — often during:
- Evening hours (e.g., 18:00–22:00)

---

## 🧠 ML Model
![image](https://github.com/user-attachments/assets/168b0800-c343-4e8f-8a10-80a324e09b72)

### Target:
- Predict crime type (`Crime_Code`) based on:
  - Time of day (`Hour`)
  - Police area (`Area_Code`)

### Classifier:
- **Random Forest Classifier**

### Evaluation:
- Accuracy Score  
- Confusion Matrix  
- Classification Report

---

## 🧪 Code Example

```python
df['Hour'] = df['TIME OCC'] // 100
le_area = LabelEncoder()
le_crime = LabelEncoder()

df['Area_Code'] = le_area.fit_transform(df['AREA NAME'])
df['Crime_Code'] = le_crime.fit_transform(df['Crm Cd Desc'])

# Train-test split
X = df[['Hour', 'Area_Code']]
y = df['Crime_Code']

X_train, X_test, y_train, y_test = train_test_split(X, y, random_state=42)
model = RandomForestClassifier(n_estimators=100)
model.fit(X_train, y_train)
