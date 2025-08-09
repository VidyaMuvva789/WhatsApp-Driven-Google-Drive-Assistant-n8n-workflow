# WhatsApp Driven Google Drive Assistant (n8n workflow)

This project is an **automation workflow** (built with n8n) that lets user manage Google Drive files using WhatsApp commands via Twilio sandbox. It supports **listing**, **deleting**, **moving**, and **summarizing** files in the given folder.

## Features
- **Google Drive control via WhatsApp** — send simple commands to manage files in google drive.
- **Supported commands:**
  - `LIST /FolderName` — list all files in the folder.
  - `DELETE /FolderName/ FileName` — delete the file in the given folder.
  - `MOVE /SourceFolder/ FileName/ DestinationFolder` — move a file from source folder to destinaton folder.
  - `SUMMARY /FolderName` — summarize the contents of each file in the folder.
- **OpenAI-powered file summaries** for PDF, DOCX, TXT files.
- **Multi-file processing** using batching/looping (Summarizes each file in the specified folder one by one).
- Receive and trigger actions via **Twilio WhatsApp messages**.

## Prerequisites
Before you begin, ensure you have:

1. **n8n** — Cloud, Self-Hosted, or Docker.
2. Enable **Google Drive API** and create API credentials.
3. **Twilio Account** with **WhatsApp Sandbox** enabled.
4. **OpenAI Account** with GPT-4 API access.

## Setup Instructions

### 1. Clone the Repository
git clone https://github.com/VidyaMuvva789/WhatsApp-Driven-Google-Drive-Assistant-n8n-workflow.git

### 2. Configure Environment Variables
- Copy `.env.sample` to `.env` and fill in your credentials:
` cp .env.sample .env `

### 3. Set up Twilio WhatsApp Sandbox
- Log in to your **Twilio account**.
- Navigate to **Messaging > Try it out > Send a WhatsApp message**.
- Activate the Sandbox and note:
   - **Sandbox number** (used as "From" in workflow)
   - **Join code** (send it from your WhatsApp to activate)
- Update your environment variables or workflow with the Twilio sandbox number.

### 4. Enable Google Drive API and Obtain Credentials
- Go to **Google Cloud Console**.
- Create a project (or select an existing one).
- Enable **Google Drive API**.
- Create **OAuth 2.0 credentials** and download the JSON file.
- Add these credentials in n8n credentials section.

### 5. Import and Configure the Workflow
- Open **n8n**.
- Import `workflow.json` from the repo.
- Link your:
   - Google Drive credentials
   - Twilio credentials
   - OpenAI credentials
- Map environment variables in nodes where needed.
  <img width="1163" height="495" alt="Image" src="https://github.com/user-attachments/assets/5e825a75-f96a-410e-83e2-8146a5062a52" />

## Command Syntax

You can control **Google Drive** by sending WhatsApp messages in the following formats:
- Commands are case-insensitive (LIST or list or List or liSt anything can be typed by user). 


| Command                | Example                          | Description                                      |
|------------------------|---------------------------------|------------------------------------------------|
| LIST /FolderName       | LIST /ProjectX                  | Lists all files in the folder(`ProjectX`). If folder(ProjectX) doesn't exist it returns `Folder doesn't exist`. If folder has no files it returns `Folder is empty.`           |
| DELETE /FolderName/FileName | DELETE /ProjectX/report.pdf     | Deletes the file `report.pdf` from folder `ProjectX`.    |
| MOVE /SourceFolder/FileName/DestinationFolder | MOVE /ProjectX/report.pdf /Archive | Moves `report.pdf` file from `ProjectX` folder to `Archive` folder. |
| SUMMARY /FolderName    | SUMMARY /ProjectX               | Summarizes the content of each file in `ProjectX` folder. |


##  Advancements to be done

- Maintain an audit spreadsheet/log to track all actions.
- Guard against accidental mass deletion (e.g., require a confirmation keyword).
