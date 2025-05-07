# Spark Loan Application Analysis 

This project analyzes Wisconsin loan application data using Apache Spark and Hive. It demonstrates loading large CSV datasets into Hive tables, transforming them with RDDs, DataFrames, and SQL, optimizing queries through bucketing and caching, and training a Decision Tree classifier to predict loan approval outcomes.

## 📚 Learning Objectives

- Use Spark's RDD, DataFrame, and SQL interfaces to process data  
- Load data into Hive and create warehouse tables/views  
- Optimize queries with techniques like bucketing and caching  
- Train and evaluate a Decision Tree model using PySpark MLlib  

---

## 🧱 Cluster Setup

This project runs on a Dockerized Spark + HDFS + Hive environment with the following containers:

- `p5-nb`: JupyterLab notebook environment  
- `p5-nn`: HDFS NameNode  
- `p5-dn`: HDFS DataNode  
- `p5-boss`: Spark Master  
- `p5-worker`: Spark Workers (2 containers)

### Build Docker Images

  ```bash
  docker build . -f p5-base.Dockerfile -t p5-base
  docker build . -f notebook.Dockerfile -t p5-nb
  docker build . -f namenode.Dockerfile -t p5-nn
  docker build . -f datanode.Dockerfile -t p5-dn
  docker build . -f boss.Dockerfile -t p5-boss
  docker build . -f worker.Dockerfile -t p5-worker
  docker compose up -d
```
## 📁 Files and Structure

1. **Clone and Build Docker Images**

- p5.ipynb: The main notebook containing all analysis and answers to Q1–Q10

- docker-compose.yml: Cluster configuration

- p5-base.Dockerfile, notebook.Dockerfile, namenode.Dockerfile, datanode.Dockerfile, boss.Dockerfile, worker.Dockerfile: Docker images

- nb/data/: Contains unzipped CSV files used in analysis

- .gitignore: To exclude large datasets from version control

## 💻 Jupyter Notebook Tasks

All answers are recorded in `p5.ipynb` with corresponding question headers as comments (e.g., `#q1`, `#q2`, ...).

### Questions

#### Part 1: Spark Interfaces

**Q1**: How many banks start with "The"? (RDD)  
**Q2**: How many banks start with "The"? (DataFrame)  
**Q3**: How many banks start with "The"? (Spark SQL)

#### Part 2: Hive Tables & Joins

**Q4**: What tables exist in the warehouse?  
**Q5**: How many loan applications did "University of Wisconsin Credit Union" receive?  
**Q6**: What does `.explain("formatted")` show for Q5?

#### Part 3: Grouping Rows

**Q7**: Average interest rates for top 10 counties where Wells Fargo receives most applications  
**Q8**: When does grouping require network I/O between partial and full aggregation?

#### Part 4: Machine Learning

**Q9**: Train 5 Decision Trees with increasing depth; report accuracy  
**Q10**: Does increasing depth always improve accuracy? Why or why not?

---

## 🛠️ Technologies Used

- Apache Spark (RDDs, DataFrames, SQL, MLlib)  
- Apache Hive  
- HDFS  
- Docker & Docker Compose  
- JupyterLab  

---

## ⚠️ Notes
  
- Data loaded to Hive tables using `.write.saveAsTable()` with bucketing on `county_code`  



