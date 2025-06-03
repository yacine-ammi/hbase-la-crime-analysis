# HBase Los Angeles Crime Data Analysis Project

This project demonstrates the process of ingesting, modeling, and querying a sample of Los Angeles crime data using Apache HBase. The primary goal is to practice fundamental NoSQL data engineering tasks, including environment setup with Docker, data exploration, HBase table design, data insertion, and querying via both the HBase Shell and Python.

## Student Information
- **Name:** Yacine Ammi
ammiyacine16@gmail.com

## Project Overview
The project follows these main stages:
1.  **Data Understanding:** Exploratory Data Analysis (EDA) of the crime dataset using Python (Pandas, Matplotlib, Seaborn).
2.  **HBase Data Modeling:** Designing an HBase namespace, table, column families, and an efficient rowkey structure.
3.  **Data Insertion:** Cleaning the data and ingesting 500,000 records into HBase using Python (`happybase`).
4.  **Querying in HBase Shell:** Retrieving specific information using HBase shell commands and filters.
5.  **Data Retrieval in Python:** Accessing and retrieving data from HBase using `happybase` in Python.

## Technologies Used
- Docker & Docker Compose
- Apache HBase (via `harisekhon/hbase` Docker image)
- Python 3.x
  - `pandas` for data manipulation
  - `happybase` for HBase interaction
  - `matplotlib` & `seaborn` for data visualization
  - `jupyterlab` or Jupyter Notebook for interactive Python tasks
- GitHub for version control and submission

## Project Structure
├── docker-compose.yml # Docker Compose configuration for HBase
├── sample_crimes_data.csv # The raw dataset (if you choose to include it)
├── eda_crime_data.ipynb # Part 1: Exploratory Data Analysis
├── hbase_insertion.ipynb # Part 3: Data Cleaning & Insertion (or .py script)
├── hbase_retrieval.ipynb # Part 5: Data Retrieval with Python (or .py script)
├── report.pdf # Final project report
└── README.md # This file


## Setup and Execution

### Prerequisites
- Docker Desktop installed and running.
- Git installed.
- Python 3.x installed.
- A Python virtual environment is highly recommended.

### 1. Clone the Repository (If applicable, for someone else running it)
If you are cloning this project:
git clone https://github.com/yacine-ammi/hbase-la-crime-analysis
cd hbase-la-crime-analysis

### 2. Create and Activate Python Virtual Environment (Recommended)
python -m venv .venv
* On Windows:
.\.venv\Scripts\activate
* On macOS/Linux:
source .venv/bin/activate

### 3. Install Python Dependencies

Install the required packages (you can create a requirements.txt file or install them directly):
pip install pandas happybase matplotlib seaborn jupyterlab
(If you create a requirements.txt file with these package names, users can run pip install -r requirements.txt)

### 4. Launch HBase Environment

Ensure Docker Desktop is running. Navigate to the project root directory (where docker-compose.yml is located) in your terminal and run:

docker-compose up -d

Wait for 2-3 minutes for HBase to fully initialize. You can check the HBase Master UI at http://localhost:16010.

### Run Python Notebooks/Scripts

Part 1 - EDA: Open and run all cells in eda_crime_data.ipynb.

Part 2 - HBase Setup (Manual Shell Steps): As per the assignment, the namespace and table are typically created via the HBase shell first.

          
    docker exec -it hbase /bin/bash
    hbase shell
    # Inside HBase shell:
    # create_namespace 'practice'
    # create 'practice:crimes', 'cf_loc', 'cf_crime', 'cf_victim'
    # exit (from hbase shell)
    # exit (from container bash)

Part 3 - Data Insertion: Open and run all cells in part 1 of hbase_insertion_retrieval.ipynb. This will connect to HBase, clean the data, and insert 500,000 rows.

Part 4 - HBase Shell Queries: These are performed manually in the HBase shell as documented in report.pdf.

Part 5 - Python Retrieval: Open and run all cells in part 2 of hbase_insertion_retrieval.ipynb to query data from HBase using Python.

View Report

The detailed project documentation, including design choices, query screenshots, and analysis, can be found in report.pdf.

### Shutdown HBase Environment

When you are finished, stop and remove the Docker containers:

docker-compose down

To also remove the HBase data volume (if you want a completely clean slate next time):

docker-compose down -v

## Notes

Ensure your system (especially if using WSL2 on Windows) has sufficient resources (RAM, CPU) allocated to Docker for HBase to run smoothly. A common recommendation for WSL2 is at least 6-8GB of RAM.

HBase Thrift server (for happybase connection) is expected to be running on localhost:9090.
