# Product Upload Automation using UiPath Studio

This project automates the process of uploading products to an online store using **UiPath Studio**, built on top of the **Robotic Enterprise Framework (REFramework)**.

It is designed for reliability, scalability, and ease of maintenance, featuring modular workflows, high-level logging, and robust exception handling.

## Demo

[Watch the Demo on YouTube](https://www.youtube.com/watch?v=VAj6RVH819g)

## Features

- Built on **Transactional Business Process** architecture (REFramework)
- **State Machine** layout for automation phases
- High-level **logging**, **exception handling**, and **auto-recovery**
- Reads **product data** from Excel (`ProductData.xlsx`)
- Pulls **credentials** from Orchestrator Assets or Windows Credential Manager
- Fetches and updates **transaction status** via Orchestrator Queues
- Captures **screenshots** on exceptions for easy debugging

## Process Flow Overview

### 1. Initialize
- `InitAllSettings.xaml`: Loads configuration from `Config.xlsx` and Orchestrator assets.
- `GetAppCredential.xaml`: Retrieves app credentials.
- `InitAllApplications.xaml`: Launches and logs into necessary applications.

### 2. Get Transaction Data
- `GetTransactionData.xaml`: Reads transaction items from an Orchestrator queue or Excel.

### 3. Process Transaction
- `Process.xaml`: Automates the product upload logic.
- Invokes helper workflows for interacting with the UI and handling business rules.

### 4. End Process
- `CloseAllApplications.xaml`: Logs out and closes all apps.
- `SetTransactionStatus.xaml`: Updates transaction status (Success, Business Exception, or System Exception).

## Project Structure

```bash
ProductUploadAutomation/
│
├── Data/                       # Input data (ProductData.xlsx) & Config.xlsx
├── Documentation/              # Any documentation, if applicable
├── Exceptions_Screenshots/     # Stores screenshots for exceptions
├── Framework/                  # Core REFramework components
├── Tests/                      # Test cases or sample invocations
├── AutoResizeSequence.xaml     # Custom logic component (e.g., resizing UI)
├── Main.xaml                   # Entry point of the automation
├── project.json                # Project metadata and dependencies
└── README.md                   # You're reading it!
