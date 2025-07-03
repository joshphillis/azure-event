# azure-event
# 📡 Azure Real-Time Event Processing Pipeline

This project demonstrates how to build a real-time data ingestion and processing pipeline using **Azure Event Hubs**, **Azure Stream Analytics**, and **Azure Blob Storage**. Simulated telecom call data is generated and streamed to the pipeline for real-time analysis and storage.

## 🚀 Project Architecture

```

Telco Data Generator → Azure Event Hub → Stream Analytics Job → Blob Storage (JSON)


## 🛠️ Tools & Technologies

- **Azure Event Hubs** – Scalable event ingestion service
- **Azure Stream Analytics** – Real-time data stream processing
- **Azure Blob Storage** – Storage for output data
- **Telco Data Generator** – Simulates telecom event data
- **Azure Resource Groups** – Logical grouping of resources
- **Shared Access Policies** – Secure access to Event Hubs

---

## 📋 Setup Steps

### 1. **Provision Azure Resources**
- Create a Resource Group: `GL-EVENT-PROC`
- Create Event Hub Namespace: `gleventproc-tio`
  - Add Event Hub: `telecomeventhub` with 2 partitions
- Create Storage Account: `gleventtio`
  - Add container: `telecomoutputstorage`
- Create Stream Analytics Job: `telecomfakecallsjob`

### 2. **Configure Stream Analytics**
- **Input:** Event Hub → `gltelecominput`
- **Output:** Blob Storage → `gltelecomoutput`
- **Query Example:**
```sql
SELECT 
    CallId,
    Caller,
    Receiver,
    Duration,
    Timestamp
INTO 
    gltelecomoutput
FROM 
    gltelecominput
````

### 3. **Generate and Send Events**

* [Download Telco Data Generator](https://aka.ms/asatelcodatagen)
* Replace placeholders in the app with:

  * **Event Hub name:** `telecomeventhub`
  * **Connection String:** from `RootManageSharedAccessKey`
* Run:

```bash
cd C:\Users\YourUsername\Downloads\TelcoGenerator\TelcoGenerator\
telcodatagen.exe 1000 0.2 2
```

### 4. **Validate Output**

* Navigate to Blob container `telecomoutputstorage`
* Confirm presence of `.json` files with event data

### 5. **Clean Up**

* Delete the resource group `GL-EVENT-PROC` to remove all resources

---

## 📂 Output Sample

```json
{
  "CallId": "93eea2d9-3b98-4f90-91bc-4a13b8d4c0f5",
  "Caller": "+15551234567",
  "Receiver": "+15559876543",
  "Duration": 12,
  "Timestamp": "2025-07-02T15:34:22Z"
}
```

---

## 📎 Notes

* Event Hub's **partition count** and **message retention** were set for basic demo needs.
* Authentication used **connection strings** for simplicity; consider managed identity in production.
* This is a foundational project suitable for extending into Power BI dashboards, Azure Functions, or Logic Apps for alerting/response.

---

## 👨‍💻 Author

**Joshua Phillis**
Cloud & Infrastructure Engineer
🔗 [LinkedIn](https://www.linkedin.com/in/joshua-phillis/)
🌐 [Portfolio](https://youractualdomainjphillxyz.xyz)

---

## 🧼 Cleanup Reminder

> Always delete your resource group when done to avoid unnecessary Azure costs.

