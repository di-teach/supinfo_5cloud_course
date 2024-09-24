# Building a unified data platform for real-time event analysis

## Project introduction

In today’s data-driven world, organizations are increasingly relying on **data platforms** to collect, manage, and analyze data in real-time.<br />
A **data platform** is an integrated solution that brings together various tools and services to ingest, process, store, and visualize data.<br />
It allows for scalable data handling and supports real-time analytics, enabling businesses to make data-driven decisions quickly and effectively.

In this project, you will design and implement a **real-time data platform** using **Microsoft Azure Fabric** services.
Your platform will ingest live or periodically updated data from any **open data source** of your choice, process it in real-time, and display insights using interactive dashboards.

This project will provide hands-on experience with key components of **Azure Fabric**: **Data Factory** for data ingestion, **Synapse Analytics** for real-time processing, and **Power BI** for visualization.

Additionally, you are encouraged to use **Python** for any data transformation, processing, or automation tasks within **Synapse Analytics** or the data pipeline.

---

## Objective

- Build a data platform that can **ingest**, **process**, and **visualize** real-time data using Microsoft Azure services.
- Choose a relevant **open data source** (e.g., sports events, stock market feeds, weather data) and design a system to provide real-time insights.
- Use **Python** when necessary for data processing or automation within the project.

---

## Steps to complete the project

### Step 1: Selecting an open data source

Begin by selecting an **open data source** that provides real-time or frequently updated data. You can use APIs or datasets from platforms like:
- **Paris 2024 data** ([Paris Open Data](https://data.paris2024.org/explore/?sort=modified))
- **Stock Market Feeds** (e.g., Alpha Vantage, Yahoo Finance)
- **Weather Data** (e.g., OpenWeatherMap)
- Etc.

Make sure to choose a source that updates frequently so you can simulate real-time analysis.

### Step 2: Setting up the data ingestion pipeline

You will use **Azure Data Factory** to ingest the selected data. Data Factory allows you to automate the extraction of data from various sources, including REST APIs, blob storage, or databases.

1. **Create an Azure Data Factory**:
    - Go to the **Azure Portal** and search for **Data Factory**.
    - Create a new **Data Factory** instance.
    - Set up a **pipeline** to periodically ingest data from your chosen open data source.

2. **Ingest Data**:
    - Use **Copy Data activity** in **Data Factory** to ingest data from your selected API or data file.
    - Configure the frequency of data ingestion (e.g., every minute or every hour).
    - Store the ingested data in **Azure Blob Storage** or directly into **Azure Synapse Analytics** for processing.

**Output**: A fully operational data ingestion pipeline that collects data from the chosen source in real-time and stores it in a cloud-based data store.

### Step 3: Real-time data processing with Synapse Analytics (Use Python)

Now that you have the data, the next step is to process it in real-time using **Azure Synapse Analytics**. You will use **Python** for data transformations or analytics within Synapse.

1. **Set up Synapse Workspace**:
    - In the **Azure Portal**, create a **Synapse Analytics Workspace**.
    - Link your **Azure Data Lake** or **Blob Storage** where the ingested data is stored.

2. **Create a Spark Pool or SQL Pool**:
    - Use **Apache Spark** (Python notebooks) or **SQL Pool** to perform real-time analysis on the ingested data.
    - Write transformation queries that clean and format the data for visualization.

3. **Process the Data with Python**:
    - If using **Spark**, you can use **Python** to write data transformation scripts.
    - Example Python code:
      ```python
      from pyspark.sql import SparkSession
 
      spark = SparkSession.builder.appName("RealTimeDataProcessing").getOrCreate()
 
      # Load the data from storage
      df = spark.read.csv("wasbs://<container>@<storage_account>.blob.core.windows.net/<file.csv>")
 
      # Perform transformations
      df_filtered = df.filter(df['column'] > 100)  # Example transformation
 
      df_filtered.show()
      ```

**Output**: Real-time data processing pipeline using Python within Synapse Analytics that transforms raw data into meaningful insights, ready for visualization.

### Step 4: Visualizing data with Power BI

Once the data is processed, it's time to create an **interactive dashboard** using **Power BI**.

1. **Connect Power BI to Synapse Analytics**:
    - Open **Power BI** and connect it to the **Azure Synapse Analytics Workspace**.

2. **Build interactive reports**:
    - Use **Power BI Desktop** to create interactive reports and dashboards that visualize key metrics from the data.
    - Examples include live event statistics, stock price movements, or weather pattern visualizations.

3. **Real-time dashboard**:
    - Enable **real-time refresh** in Power BI so that your dashboards update automatically as new data is processed.

**Output**: A live, interactive Power BI dashboard that showcases real-time insights based on the ingested and processed data.

---

## Bonus: Infrastructure as Code (IaC) with Terraform

As a bonus, you can implement **Infrastructure as Code** (IaC) using **Terraform** to automate the deployment of your Azure resources.<br />
This includes deploying **Azure Data Factory**, **Synapse Analytics**, and **Power BI** components.

1. **Set up Terraform**:
    - Use the **Microsoft Fabric Terraform provider**: [Terraform Azure Fabric Provider](https://registry.terraform.io/providers/microsoft/fabric/latest/docs).

2. **Write Terraform configuration**:
    - Define your infrastructure in a `.tf` file, including the deployment of Data Factory, Synapse Analytics, and other resources needed for your data platform.

3. **Deploy the infrastructure**:
    - Run Terraform commands to provision the Azure resources automatically.

**Example Terraform snippet**:
```hcl
provider "azurerm" {
  features {}
}

resource "azurerm_synapse_workspace" "example" {
  name                = "synapse-workspace"
  resource_group_name = "example-resources"
  location            = "West Europe"
}

resource "azurerm_synapse_spark_pool" "example" {
  name                 = "synapse-spark-pool"
  synapse_workspace_id = azurerm_synapse_workspace.example.id
  node_size_family     = "MemoryOptimized"
  node_size            = "Small"
}
