# File Integrity Monitor

## Overview
This Python script monitors file integrity in a specified folder by calculating file hashes and detecting changes (modifications, new files, or deletions). If a change is detected, it logs the event and automatically creates a Jira ticket for further investigation.

## Features
- Monitors a folder for file changes (modifications, additions, deletions)
- Logs all integrity checks and issues
- Automatically creates Jira tickets for detected changes
- Stores file hashes in a JSON file for comparison

## Requirements
Ensure you have the following dependencies installed:

```bash
pip install -r requirements.txt
```

### Dependencies
- `os` (built-in) - Interacts with the operating system
- `hashlib` (built-in) - Computes file hashes
- `json` (built-in) - Handles JSON operations
- `time` (built-in) - Provides real-time operations
- `logging` (built-in) - Logs events and errors
- `schedule` - Schedules periodic execution
- `requests` - Sends HTTP requests (for Jira API)
- `python-dotenv` - Loads environment variables

To install missing dependencies:

```bash
pip install schedule requests python-dotenv
```

## Setup & Configuration
### 1. Clone the Repository
```bash
git clone https://github.com/your-username/FileIntegrityMonitor.git
cd FileIntegrityMonitor
```

### 2. Set Up Environment Variables
Create a `.env` file in the project directory:

```bash
touch .env
```
Add your Jira credentials:

```ini
JIRA_EMAIL=your_email@example.com
JIRA_API_KEY=your_api_key
```

### 3. Define Folder to Monitor
Update `FOLDER_TO_MONITOR` in the script with the folder path you want to monitor:
```python
FOLDER_TO_MONITOR = r"/path/to/your/folder"
```

### 4. Run the Script
```bash
python file_integrity_monitor.py
```

## How It Works
1. **Initial Scan**: The script calculates hashes for all files in the folder and saves them.
2. **Change Detection**:
   - If a file is modified, a warning is logged and a Jira ticket is created.
   - If a new file is added, it is logged and a Jira ticket is created.
   - If a file is removed, it is logged and a Jira ticket is created.
3. **Scheduled Execution**: The script can be run periodically using `schedule`.

## License
This project is licensed under the MIT License.

## Author
Created by **Ashique**. Contributions are welcome!

