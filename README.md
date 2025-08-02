# 🎓 Student Feedback ETL Pipeline using Azure Data Factory

This project demonstrates a batch ETL pipeline using Azure Data Factory (ADF) to extract student feedback from Azure Data Lake (ADLS Gen2), 
filter the data using **Mapping Data Flow** (`rating >= 4`), and load the transformed data into Azure SQL Database for analysis.

## 💻 Tech Stack
- Azure Data Factory (ADF)
- Mapping Data Flow
- Azure Data Lake Storage Gen2
- Azure SQL Database
- SQL for analysis

## 📁 Project Structure

student-feedback-etl-adf/
│
├── pipeline/     
│   └── student_feedback_pipeline.json    
├── datasets/
|   └── DS_SFeedback_CSV
|   └── DS_Sfeedback_SQL
├── LinkedServices/
│   └── LS_ADLS
│   └── LS_ASQL
|
├── data/
│   └── feedback_sample.csv                     
│
├── sql/
│   └── schema.sql              
│
├── images/
│   ├── adf_pipeline_flow.png           
│   ├── dataflow_pipeline.png                     
│   └── pipeline_runs_successfully.png     
|
├── Readme.md

## 🔄 ETL Flow

1. **Extract**: Student feedback CSV from ADLS Gen2  
2. **Transform**: Mapping Data Flow filters feedback where `rating >= 4`  
3. **Load**: Transformed data into Azure SQL Database  
4. **Analyze**: Run SQL queries to get course ratings and insights

## 📌 Data Flow Logic (Filter on Rating)

In ADF Data Flow:
- A **Derived Column** is added:
  ```plaintext
  rating_int = toInteger(rating)
