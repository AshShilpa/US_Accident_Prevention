# 🚗 Car Accidents Prevention Using Spark & Spark.ML  

## 📌 Project Overview  
Vehicular accidents result in significant fatalities and injuries globally. This project aims to develop a **machine-learning model** capable of predicting accident hotspots based on real-time traffic conditions. By leveraging **big data analytics** and **Apache Spark**, we analyze accident trends to enhance road safety and assist first responders.  

## 🏆 Motivation  
- **Global Road Safety**: WHO reports 1.3M deaths annually due to road traffic crashes.  
- **Data-Driven Insights**: Identify accident-prone areas based on historical data.  
- **Emergency Preparedness**: Aid first responders by predicting high-risk zones.  
- **Driver Awareness**: Provide real-time accident risk information to drivers.  

---   

## ⚙️ Implementation Pipeline  

### **1. Data Preprocessing & Cleaning**  
- Removed duplicate rows and missing values.  
- Scaled numerical features for consistency.  
- Used dimensionality reduction techniques to retain critical information.  

### **2. Data Analysis & Visualization**  
- **State-wise accident aggregation**: Identified regions with highest accident rates.  
- **Temporal analysis**: Explored accident frequency across time (hourly, daily, monthly).  
- **Geospatial visualization**: Mapped accident hotspots across the U.S.  
- **Weather impact analysis**: Examined correlation between accidents and weather conditions.  

### **3. Machine Learning Models**  
We evaluated multiple ML models to identify the most effective approach for accident prediction.  

| Model                           | Accuracy | Precision | Recall | F1-Score |
|--------------------------------|----------|-----------|--------|----------|
| **Random Forest Classifier**   | 83.05%   | 0.6897    | 0.8305 | 0.7536   |
| **Gradient Boosted Trees**     | -        | -         | -      | RMSE: 0.4397, MAE: 0.2808 |
| **PCA & Linear Regression**    | -        | -         | -      | RMSE: 0.4574, MAE: 0.3049 |

**Best Model**: The **Random Forest Classifier** achieved the highest accuracy (83.05%) and provided reliable predictions.  

---

## 🔍 Key Findings  
- **California, Florida, and Texas account for most accidents** (~42% of total).  
- **Accidents peak during late-night hours (9 PM - 1 AM)** and afternoon rush hours.  
- **Severe accidents are more frequent in colder months (Nov-Jan)**.  
- **Lower temperature, wind chill, and humidity increase accident severity**.  

---

## 🛠 Tech Stack  
- **Programming Language**: Python 🐍 & Scala  
- **Big Data Processing**: Apache Spark & Spark ML  
- **Machine Learning**: Scikit-Learn, Spark MLlib  
- **Visualization**: Matplotlib, Seaborn  

---
## 🔧 Dependencies Installation  
Ensure all dependencies listed in the `pom.xml` file are installed. If not, add them and reload the Maven project. Then execute the following Maven command:

```bash
mvn clean install
```

---

## 📊 Data Setup  
📥 Place the original **CSV data** in the following location:  
```
data/input/original_data.csv
```

---

## 🧹 Data Cleaning  
To clean the data, follow these steps:

1. Open the file:
   ```
   src/main/scala/edu/ucr/cs/cs226/vchin014/App.scala
   ```
2. Uncomment the following line:
   ```scala
   Cleaning.cleanData(spark, inputPath, cleanedDataPath)
   ```

---

## 🔄 Data Transformation  
To transform the cleaned data before applying machine learning algorithms, perform the following:

1. In `App.scala`, uncomment the following line:
   ```scala
   DataFrameTransformation.transformation(spark, cleanedDF, dataFrameTransformationPath)
   ```

---

## 🤖 ML Algorithm Application  

- **🌲 RandomForest Classifier:**  
  Uncomment the following line in `App.scala`:
  ```scala
  codeAlgorithms.applyAlgorithms(spark, transformedDF)
  ```

- **🚀 GBT Regression:**  
  Uncomment the following line:
  ```scala
  GbtAlgorithm.applyAlgorithms(spark, transformedDF)
  ```

- **📉 PCA-Linear Regression:**  
  Uncomment the following line:
  ```scala
  PcaAlgorithm.applyAlgorithms(spark, transformedDF)
  ```

---

## 🚀 Execution  

### **📦 Building the JAR**  
Build and package your code into a JAR file (`spark-sql-1.0-SNAPSHOT.jar`) using the following Maven command:

```bash
mvn package
```

### **🏎️ Running the Application**  
Run the application using the `spark-submit` command:

```bash
spark-submit \
  --master "local[*]" \
  --executor-memory 16G \
  --driver-memory 10G \
  --conf spark.driver.memoryOverhead=4G \
  --conf spark.executor.memoryOverhead=4G \
  --conf spark.driver.maxResultSize=8G \
  --conf spark.sql.shuffle.partitions=32 \
  --conf spark.default.parallelism=32 \
  --conf "spark.executor.extraJavaOptions=-XX:+UseG1GC -XX:InitiatingHeapOccupancyPercent=35 -XX:ConcGCThreads=2" \
  target/spark-sql-1.0-SNAPSHOT.jar
```

**⚠️ Note:** Adjust the `spark-submit` parameters according to your system configuration.


## ⭐ Contribute & Support  
🌟 If you found this project helpful, consider giving it a ⭐ on GitHub!  
📢 Feel free to fork and contribute to improve road safety with **AI-driven insights**.

---

