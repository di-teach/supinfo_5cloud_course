## Hands-on Exercise: Cloud Cost Management and Resource Optimization

Let's explore how to optimize cloud costs using **Azure Cost Management** tools and strategies like auto-scaling, reserved instances, and monitoring usage. We'll use **Paris 2024 data** (e.g., event schedules, venue data, ticket sales) to simulate real-world scenarios of cloud cost management.

### Objective

Optimize cloud resources and manage costs using **Azure Cost Management**, focusing on cost-saving strategies, resource scaling, and monitoring while processing **Paris 2024 Olympic Games data**.

### Step-by-Step Guide

---

### **Step 1: Analyze Costs with Azure Cost Management**

**Objective**: Use **Azure Cost Management** to analyze your cloud usage and identify areas where costs can be optimized while processing **Paris 2024 datasets**.

- **Navigate to Azure Cost Management**:
  - Go to the **Azure Portal** and search for **Cost Management + Billing**.
  - Select **Cost Management** from the menu.
- **View Cost Breakdown**:
  - Access the **Cost Analysis** tab to view your cost breakdown by service, resource group, or subscription.
  - Filter by date to check your cloud spend over the past month or week.
  - Identify the most expensive resources (e.g., VMs, storage, networking) used for analyzing **Paris 2024 data**.

**Expected Result**: You’ll have a clear breakdown of your current cloud costs, identifying which resources are consuming the most budget when processing **Paris 2024 data**.

---

### **Step 2: Implement Auto-Scaling for VMs**

**Objective**: Implement **auto-scaling** to adjust resource capacity automatically based on demand, preventing over-provisioning and saving costs while processing **Paris 2024 data**.

- **Navigate to Virtual Machine Scale Sets**:
  - In the Azure portal, go to **Virtual Machines** and select your virtual machine.
  - Under **Settings**, select **Scale Sets**.
- **Create an Auto-Scaling Policy**:
  - Define rules to scale out (add VMs) when CPU utilization exceeds 75% during the processing of **Paris 2024 datasets**.
  - Define rules to scale in (remove VMs) when CPU utilization drops below 30%.
  - Set a minimum and maximum number of instances.
- **Apply Auto-Scaling**:
  - Save the settings and test the auto-scaling behavior by applying a workload related to **Paris 2024 data** to the VMs.

**Expected Result**: The virtual machines will automatically scale up or down based on the workload, optimizing resource usage and reducing costs while processing the **Paris 2024 Olympic Games datasets**.

---

### **Step 3: Set Up Budget Alerts**

**Objective**: Create a budget in **Azure Cost Management** and set alerts to notify you when your cloud spending on **Paris 2024 data processing** approaches a predefined threshold.

- **Navigate to Budgets**:
  - In the **Azure Portal**, go to **Cost Management + Billing** and select **Budgets**.
- **Create a New Budget**:
  - Set a **monthly budget** for your project (e.g., $500) to analyze **Paris 2024 data**.
  - Define **alert thresholds** at 80%, 90%, and 100% of the budget.
  - Set up **email notifications** to alert you when the budget limit is nearing.

**Expected Result**: You will receive notifications when your cloud spending on **Paris 2024 data processing** reaches the predefined thresholds, helping you stay within budget.

---

### **Step 4: Optimize Storage Costs with Tiered Storage**

**Objective**: Move infrequently accessed **Paris 2024 data** (e.g., older event schedules) to a lower-cost storage tier (e.g., **Azure Blob Storage Archive**).

- **Navigate to Blob Storage**:
  - In the Azure portal, open **Storage Accounts** and select a **Blob Storage** account.
- **Select Data for Archiving**:
  - Move the data to **Archive tier**, which offers lower costs for long-term storage.

**Expected Result**: The selected **Paris 2024 data** will be archived in a lower-cost tier, reducing storage expenses without compromising data availability.

> In real situation, we should for example identify data that has not been accessed in over 30 days (e.g., historical event schedules).

---

### **Summary of the Activity**

In this exercise, you have learned how to:
1. Analyze your cloud spending using **Azure Cost Management** while processing **Paris 2024 data**.
2. Implement **auto-scaling** to optimize VM resources.
3. Set up **budget alerts** to monitor cloud spending on **Paris 2024 datasets**.
4. Optimize storage costs using **tiered storage** strategies.

This hands-on session demonstrates how to effectively manage and optimize cloud resources and costs while analyzing **Paris 2024 Olympic Games data** using **Azure Cost Management** tools.