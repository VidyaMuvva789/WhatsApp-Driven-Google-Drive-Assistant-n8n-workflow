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
- **Multi-file processing** using batching/looping.
- Receive and trigger actions via **Twilio WhatsApp messages**.

## Setup Instructions

### Clone the Repository
https://github.com/VidyaMuvva789/WhatsApp-Driven-Google-Drive-Assistant-n8n-workflow.git
