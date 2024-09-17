# Introduction do cloud data services

Let's deploy and manage a data cluster on Azure HDInsight.

## Objective

Deploy an Apache Spark cluster on Azure HDInsight and manage it to process a sample big data workload.

### Step-by-Step Guide

**Create an Azure HDInsight Cluster:**

- Navigate to the Azure Portal
  - Go to the Azure Portal.
- Create a New HDInsight Cluster
  - In the Azure portal, select "Create a resource" and search for "HDInsight". 
  - Click on "Apache Spark Cluster" and then "Create."
- Configure the Cluster
  - Basics
    - Choose your Subscription and Resource Group. 
    - Enter a Cluster name (e.g., spark-cluster-demo). 
    - Select Cluster type: Choose "Spark."
    - Select Version: Choose a supported Spark version (e.g., Spark 3.0).
  - Cluster Size
    - Define the number of worker nodes and the VM size for each node. 
    - For testing purposes, you can use a smaller cluster with fewer nodes.
  - Storage
    - Choose a storage account. You can either create a new one or use an existing Azure Blob Storage account. 
    - Security + Networking:
    - Configure network settings and cluster access permissions. 
  - Review + Create
    - Review the configuration and click "Create" to deploy the cluster. It may take several minutes for the cluster to be provisioned.

**Upload Data to Azure Storage:**

- Navigate to Azure Storage Account
  - Go to the Azure portal, and open the storage account associated with your HDInsight cluster. 
- Upload Data:
  - In the storage account, go to "Containers" and select a container (or create a new one). 
  - Click "Upload" to add your data files (e.g., a CSV file for data processing).

**Run a Spark Job on the Cluster:**

- Access the Cluster
  - In the Azure portal, navigate to your HDInsight cluster and select "Cluster Dashboard."
- Submit a Spark Job
  - Use the Jupyter Notebook or SSH into the cluster to submit a Spark job.
  - For example, using PySpark
    ```python
    from pyspark.sql import SparkSession
    spark = SparkSession.builder.appName("example").getOrCreate()
    # Load data from Azure Blob Storage
    df = spark.read.csv("wasbs://<container>@<storage_account>.blob.core.windows.net/<file.csv>")
    # Perform simple transformation
    df_filtered = df.filter(df['_c0'] > 100) # Example filtering
    df_filtered.show()
    ```
  - Monitor the Job
    - Monitor job progress via the Apache Ambari dashboard, accessible through the cluster's dashboard link in the Azure portal.

**Manage the Cluster**

- Scale the Cluster
  - In the Azure portal, navigate to your HDInsight cluster and select "Scale Cluster."
  - Adjust the number of worker nodes to scale the cluster up or down based on your workload. 
- Monitor Cluster Health
  - Use Azure Monitor and Apache Ambari to keep track of cluster health, performance metrics, and logs. 
- Secure the Cluster
  - Implement security practices such as Azure Active Directory integration and role-based access control (RBAC).