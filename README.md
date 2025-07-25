# azure-event
# 📡 Azure Real-Time Event Processing Pipeline

This project demonstrates how to build a real-time data ingestion and processing pipeline using **Azure Event Hubs**, **Azure Stream Analytics**, and **Azure Blob Storage**. Simulated telecom call data is generated and streamed to the pipeline for real-time analysis and storage.

## 🚀 Project Architecture
# 📡 Azure Event Processing Pipeline: Telecom Call Simulator

## Overview
This project demonstrates an end-to-end pipeline using **Azure Event Hubs**, **Stream Analytics**, and **Blob Storage** to ingest and process simulated telecom call data. Built by Joshua Phillis, the solution showcases real-time data streaming and secure resource provisioning using Azure-native tools.

---

## 💡 Architecture Summary

| Component             | Description                                      |
|----------------------|--------------------------------------------------|
| Event Hub Namespace  | `gleventproc-tio`                                |
| Event Hub Name       | `telecomeventhub`                                |
| Stream Analytics Job | `telecomfakecallsjob`                            |
| Input Alias          | `gltelecominput` (from Event Hub)                |
| Output Alias         | `gltelecomoutput` (to Blob storage)              |
| Storage Container    | `telecomoutputstorage` in `gleventtio` account   |

---

## 🚀 Deployment Steps

### 1. Provision Core Resources
- ✅ Create Resource Group: `GL-EVENT-PROC`
- ✅ Deploy Event Hub namespace: `gleventproc-tio`
- ✅ Create Event Hub: `telecomeventhub` (2 partitions, 1-day retention)
- ✅ Set up Storage Account: `gleventtio` with LRS redundancy
- ✅ Create Blob container: `telecomoutputstorage`

### 2. Configure Stream Analytics Job
- 🔄 Job Name: `telecomfakecallsjob`
- 🔌 Input: Event Hub (`gltelecominput`)
- 📤 Output: Blob Storage (`gltelecomoutput`)
- ✍️ Query: Extract call data using custom SQL logic

### 3. Generate Sample Data
- 🔗 Download simulator: [Telco Data Generator](https://aka.ms/asatelcodatagen)
- 🖥️ Run:
  ```shell
  cd C:\xxxxxx\xxxxxx\xxxxxx\TelcoGenerator\TelcoGenerator\
  telcodatagen.exe 1000 0.2 2

## 👨‍💻 Author

**Joshua Phillis**
Cloud & Infrastructure Engineer
🔗 [LinkedIn](https://www.linkedin.com/in/joshua-phillis/)


---

## 🧼 Cleanup Reminder

> Always delete your resource group when done to avoid unnecessary Azure costs.

