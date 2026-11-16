# DWBA Assignments – Debottam Sarkar

This repository contains the assignments, practical implementations, and analytical projects completed as part of the **Data Warehousing and Business Analytics (DWBA)** course during the 5th semester of B.Tech at Sikkim Manipal Institute of Technology (SMIT).

The repository consists of five assignments covering data preprocessing, business analytics, MapReduce programming, multivariate statistical analysis, Principal Component Analysis (PCA), clustering, Apache Spark, and Structured Streaming.

Each assignment contains its respective source code, datasets, Jupyter Notebooks, analytical outputs, and implementation files.

---

## 📂 Repository Structure

```text
DWBA-ASSIGNMENT-DEBOTTAM-SARKAR-202400303/
│
├── Assignment1/
│   ├── DWBA MBA ANALYSIS/
│   └── online_retail_france.csv
│
├── Assignment 2/
│   ├── all_subjects_grades.txt
│   ├── grade_distribution_by_subject.csv
│   ├── grade_distribution_chart.png
│   ├── mapper.py
│   ├── metadata[1].json
│   ├── prepare_data.py
│   ├── reducer.py
│   └── run_mapreduce.py
│
├── Assignment 3/
│   └── class3.ipynb
│
├── Assignment 4 Multivariate Analysis.ipynb
│
├── Assignment 5 SparkStreaming.ipynb
│
└── README.md
```

---

# 📘 Assignment 1 – MBA Analysis

The Assignment1 folder contains the work completed for the first DWBA assignment, focusing on business analysis and data exploration.

### Files and Folders

- **DWBA MBA ANALYSIS/** – Contains the analysis and related work performed for the MBA analysis component.
- **online_retail_france.csv** – Dataset containing online retail transaction information used for performing data analysis and deriving business insights.

### Key Concepts
- Business Data Analysis
- Data Exploration
- Dataset Processing
- Business Intelligence
- Analytical Interpretation

---

# 📗 Assignment 2 – MapReduce-Based Grade Distribution Analysis

Assignment 2 focuses on implementing a MapReduce-based data-processing workflow to analyse grade distributions across different subjects.

The implementation consists of Python scripts for data preparation, mapping, reducing, and execution, along with the generated analytical outputs.

### Files and Their Functionality

**1. prepare_data.py – Data Preparation**

Responsible for preparing and processing the input dataset before executing the MapReduce workflow.

**2. mapper.py – Mapper Stage**

Implements the Mapper component of the MapReduce programming model. It processes input records and generates intermediate key-value pairs.

**3. reducer.py – Reducer Stage**

Implements the Reducer component, processing intermediate key-value pairs and performing the required aggregation.

**4. run_mapreduce.py – Execution Script**

Coordinates the different stages of the MapReduce workflow and generates the final analytical results.

**5. metadata[1].json**

Contains supporting metadata associated with the dataset or processing task.

### Generated Outputs

- **all_subjects_grades.txt** – Contains processed grade information for different subjects.
- **grade_distribution_by_subject.csv** – Contains the calculated grade distribution for different subjects.
- **grade_distribution_chart.png** – Graphical representation of the grade distribution.

### Key Concepts
- MapReduce Programming Model
- Mapper and Reducer Operations
- Data Preprocessing
- Key-Value Pair Processing
- Data Aggregation
- Python-Based Data Processing
- Data Visualization

---

# 📕 Assignment 3 – Data Warehousing and Business Analytics

Assignment 3 contains the practical implementation and analysis performed using Jupyter Notebook.

### File

**class3.ipynb**

This notebook contains the implementation and analytical work for Assignment 3.

It can be executed using:
- Jupyter Notebook
- JupyterLab
- Google Colab

---

# 📙 Assignment 4 – Sales Analysis and Multivariate Statistical Analysis

Assignment 4 focuses on applying data analytics, distributed data processing, dimensionality reduction, clustering, and statistical analysis to different datasets.

The implementation is available in:

**Assignment 4 Multivariate Analysis.ipynb**

The notebook is divided into three major analytical components.

### 1. Quantity Sold Across Product Categories

This section uses the **Kaggle Sample Sales Data** dataset to analyse product-category-wise sales.

The analysis considers completed transactions with the status `Shipped` and calculates the total quantity sold across different product categories.

**Key Operations:**
- Loading and processing sales transaction data.
- Filtering completed and shipped orders.
- Grouping transactions by product category.
- Calculating total units sold.
- Generating a category-wise sales visualization.

**Technologies:** PySpark, Pandas, Matplotlib.

Dataset: [Kaggle – Sample Sales Data](https://www.kaggle.com/datasets/kyanyoga/sample-sales-data)

### 2. Multivariate Analysis of Wine Measurements

This section performs multivariate statistical analysis using the **UCI Wine Dataset**, which consists of 178 wine samples and 13 chemical measurements.

The implementation applies Principal Component Analysis (PCA) to reduce dimensionality while retaining at least 90% of the total variance.

Hierarchical clustering using Ward linkage is then performed on the retained principal components.

The optimal number of clusters is selected by comparing silhouette scores for cluster counts ranging from 2 to 5.

**Key Operations:**
- Standardization of numerical features.
- Principal Component Analysis (PCA).
- Explained variance analysis.
- Ward Hierarchical Clustering.
- Silhouette Score Evaluation.
- Cluster Visualization.
- Comparison with known wine cultivar labels.

**Technologies:** Python, Scikit-learn, NumPy, Pandas, Matplotlib.

Dataset: [UCI Wine Dataset](https://archive.ics.uci.edu/dataset/109/wine)

### 3. Subject-Wise Grade Distribution and Student Performance Analysis

This section analyses student marks across multiple subjects and calculates grade distributions.

The implementation supports uploading an actual student marks CSV file. When no dataset is provided, it uses 24 simulated student records for demonstration.

Spark's `map()` and `reduceByKey()` operations are used to calculate subject-wise grade counts.

PCA is also applied to standardized student marks to identify patterns and differences in performance across subjects.

**Key Operations:**
- Student marks preprocessing.
- Subject-wise grade classification.
- Overall student grade calculation.
- MapReduce-based grade aggregation using Spark.
- PCA using Singular Value Decomposition (SVD).
- Grade distribution visualization.
- Student performance pattern analysis.

**Technologies:** PySpark, Pandas, NumPy, Matplotlib.

### Key Concepts Covered
- Business Analytics
- Sales Data Analysis
- Distributed Data Processing
- Multivariate Statistical Analysis
- Dimensionality Reduction
- Principal Component Analysis (PCA)
- Hierarchical Clustering
- Silhouette Score
- Data Standardization
- Student Performance Analytics
- Data Visualization

---

# 📒 Assignment 5 – Apache Spark Structured Streaming

Assignment 5 focuses on implementing a fault-tolerant order-processing pipeline using **Apache Spark Structured Streaming**.

The project demonstrates how incoming order data can be processed continuously, validated, deduplicated, and stored in a transactional SQLite database.

The notebook deliberately introduces a failure after a database batch has been committed and then resumes processing using the same Spark checkpoint.

The objective is to demonstrate checkpoint-based recovery, duplicate prevention, and transactional consistency during streaming failures.

### Project: Recovering a Shop Order Stream

**Implementation:** Assignment 5 SparkStreaming.ipynb

### 1. Streaming Environment Setup

- Configuring Apache Spark.
- Initializing Spark Structured Streaming.
- Creating isolated input, staging, checkpoint, and database directories.
- Initializing an SQLite transaction ledger.

### 2. Publishing Order Data

The implementation generates simulated shop orders across three departments:

- Books
- Stationery
- Electronics

Three separate deliveries are published, containing 18 distinct orders along with duplicate and invalid records.

The incoming JSON files are published through a staging directory to ensure that files are completely written before being processed.

### 3. Data Validation and Deduplication

Spark Structured Streaming processes the incoming JSON records.

The pipeline performs:
- JSON schema validation.
- Detection of malformed records.
- Validation of order IDs and timestamps.
- Filtering of invalid quantities and prices.
- Event-time watermarking.
- Duplicate removal using order IDs.

A two-minute watermark is applied to bound the streaming deduplication state.

### 4. Transactional Data Storage

The processed order records are stored in an SQLite database using `foreachBatch()`.

Two database tables are maintained:

- `orders` – Stores the processed order information.
- `processed_batches` – Tracks successfully committed batch IDs.

Database transactions ensure that order records and their corresponding batch IDs are committed together.

### 5. Failure Simulation and Recovery

A controlled failure is deliberately introduced after the second delivery has been committed to the SQLite database.

The streaming query is then restarted using the same checkpoint.

The implementation verifies that:
- Previously committed batches are not duplicated.
- Unfinished batches can be replayed.
- The streaming query resumes using its existing checkpoint.
- All original order records are recovered correctly.

### 6. Validation and Results

The final implementation performs several validation checks:

- Verification of all 18 unique orders.
- Comparison of recovered records against the original generated input.
- Duplicate order detection.
- Department-wise order and revenue aggregation.
- Verification of committed batch IDs.
- Confirmation that restarting without new input does not change the ledger.

### Technologies Used
- Apache Spark
- PySpark Structured Streaming
- Python
- SQLite
- Pandas
- JSON
- Spark Checkpointing
- Transaction Management

### Key Concepts Covered
- Real-Time Data Processing
- Apache Spark Structured Streaming
- Micro-Batch Processing
- Event-Time Watermarking
- Data Validation
- Deduplication
- Fault Tolerance
- Checkpoint-Based Recovery
- Transactional Data Storage
- Failure Handling
- Data Consistency

**Important Note:** The project uses simulated order data and demonstrates recovery while the local runtime files remain available. Persistent recovery after deleting the Colab runtime would require independently persistent storage for the input files, database, and checkpoint.

---

# 🛠️ Technologies and Tools Used

The five assignments collectively explore the following technologies and concepts:

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Notebook Environment | Jupyter Notebook, Google Colab |
| Distributed Processing | Apache Spark, PySpark |
| Data Processing | Pandas, NumPy |
| Statistical Analysis | Scikit-learn |
| Dimensionality Reduction | PCA, SVD |
| Machine Learning | Hierarchical Clustering |
| Data Visualization | Matplotlib |
| Streaming | Spark Structured Streaming |
| Database | SQLite |
| Data Formats | CSV, JSON, TXT |
| Processing Model | MapReduce |
| Data Recovery | Spark Checkpointing |

---

# ▶️ Running the Assignments

### Assignment 2 – Python MapReduce Implementation

Make sure Python 3 is installed.

Run the following commands from the repository's root directory:

```bash
python "Assignment 2/prepare_data.py"
python "Assignment 2/run_mapreduce.py"
```

The individual Mapper and Reducer scripts can also be executed separately when required.

```bash
python "Assignment 2/mapper.py"
python "Assignment 2/reducer.py"
```

### Assignment 4 – Multivariate Analysis

Open `Assignment 4 Multivariate Analysis.ipynb` using Google Colab or Jupyter Notebook.

Install the required dependencies:

```bash
pip install pyspark==4.0.1 pandas==2.2.3 numpy==2.2.6 scikit-learn==1.6.1 matplotlib==3.10.0
```

Run all notebook cells sequentially.

For the sales analysis, the notebook downloads the Kaggle dataset automatically. If downloading fails, upload `sales_data_sample.csv` manually.

The student performance section uses simulated marks by default. An actual marks CSV can be provided by setting the `RESULTS_CSV` variable.

### Assignment 5 – Spark Structured Streaming

Open `Assignment 5 SparkStreaming.ipynb` using Google Colab or Jupyter Notebook.

Install the required dependencies:

```bash
pip install pyspark==4.0.1 pandas==2.2.3
```

Run all notebook cells sequentially in a fresh Python runtime.

The notebook automatically generates simulated order data, processes streaming batches, introduces a controlled failure, and validates checkpoint-based recovery.

---

# 🎯 Learning Objectives

Through these five assignments, the following concepts are explored:

- Data Warehousing and Business Analytics.
- Data Preprocessing and Transformation.
- Business Data Analysis and Interpretation.
- MapReduce Programming Model.
- Distributed Data Processing.
- Data Aggregation and Visualization.
- Multivariate Statistical Analysis.
- Principal Component Analysis.
- Hierarchical Clustering.
- Dimensionality Reduction.
- Student Performance Analytics.
- Apache Spark and PySpark.
- Structured Streaming.
- Event-Time Processing and Watermarking.
- Data Deduplication and Validation.
- Fault Tolerance and Checkpoint Recovery.
- Transactional Data Management.

---

# 👨‍💻 Author

**Debottam Sarkar**

B.Tech – Computer Science and Engineering  
Sikkim Manipal Institute of Technology (SMIT)

Registration Number: 202400303

---

### 📌 Academic Note

This repository contains academic coursework, practical implementations, and analytical projects completed as part of the Data Warehousing and Business Analytics (DWBA) course.

The repository is intended to document the practical application of data analytics, distributed computing, statistical analysis, and streaming technologies.
