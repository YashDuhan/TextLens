# TextLens - Full-Stack PDF Question Answering Application

TextLens is a web application where users can upload PDF files, ask questions about their contents, and receive accurate responses. It leverages FastAPI for the backend, PyMuPDF for text extraction, AWS S3 for file storage, and a React.js frontend for a seamless user experience.

## Repositories

- **Frontend Repository**: [TextLens-Frontend](https://github.com/YashDuhan/TextLens-Frontend.git)
- **Backend Repository**: [TextLens-Backend](https://github.com/YashDuhan/TextLens-Backend.git)

---

## Table of Contents

- [Features](#features)
- [Technologies](#technologies)
- [Architecture Overview](#architecture-overview)
- [Project Setup](#project-setup)
- [API Documentation](#api-documentation)
- [Hosting](#hosting)
- [Usage](#usage)
- [Project Architecture](#project-architecture)

## Features

- Upload PDF files and extract text from the document.
- Store PDFs in AWS S3 for long-term access.
- Ask questions about uploaded PDFs and receive AI-powered answers.
- Clear previous conversations to start fresh.

## Technologies

- **Backend**: FastAPI, SQLAlchemy, AWS S3, PyMuPDF
- **Frontend**: React.js, TailwindCSS
- **Database**: PostgreSQL
- **NLP Model**: Llama 3.2

## Architecture Overview

The application consists of two main parts:

- **Backend**: FastAPI handles PDF uploads, stores metadata, and manages the question-answering functionality. Files are stored in AWS S3, and metadata is stored in a PostgreSQL database.
- **Frontend**: Built with React, the frontend provides an interactive user interface to upload PDFs, get permanent S3 link, and communicate with the AI.

## Project Setup

### Prerequisites

- Python 3.8+
- Node.js and npm
- PostgreSQL database
- AWS S3 bucket with credentials
- GROQ API key for NLP processing

### Backend Setup

1. Clone the backend repository:

   ```bash
   git clone https://github.com/YashDuhan/TextLens-Backend.git
   ```

2. Install dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Set environment variables in a `.env` file:

   ```
   DATABASE_URL=
   AWS_ACCESS_KEY_ID=
   AWS_SECRET_ACCESS_KEY=
   S3_BUCKET_NAME=
   S3_REGION=
   GROQ_API_KEY=
   ```

4. Run the FastAPI backend:
   ```bash
   uvicorn app.main:app --reload
   ```

### Running the Project with Docker

1. **Build the Docker image**:

   ```bash
   docker build -t textlens-app .
   ```

2. **Run the Docker container**:
   ```bash
   docker run -p 8000:8000 textlens-app
   ```

### Frontend Setup

1. Clone the frontend repository:

   ```bash
   git clone https://github.com/YashDuhan/TextLens-Frontend.git
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Run the frontend:
   ```bash
   npm run dev
   ```

## API Documentation

#### POST `/upload`

Upload a PDF file to extract text and store it in AWS S3.

- **Body**: `file (UploadFile)`: PDF file to upload.
- **Response**: `{ filename, extracted_text, s3_url }`

#### POST `/ask`

Ask a question about the uploaded PDF content.

- **Body**:
  - `extracted_text (str)`: Extracted text from the PDF.
  - `question (str)`: The question to ask.
  - `previous_convo (list[list[str]])`: Previous questions in conversation format.
- **Response**: `{ answer }`

## Hosting

- **Frontend**: Hosted on Vercel at https://textlens.vercel.app/
- **Backend**: Hosted on Vercel at https://text-lens-backend.vercel.app/docs

## Usage

1. Open the frontend in a browser.
2. Upload a PDF file.
3. Ask questions about the content, and see responses from the AI.
4. Clear chat if needed to start a new session.

## Project Architecture

For a detailed view of the project's architecture, refer to the following document:

[Project Architecture](https://docs.google.com/document/d/e/2PACX-1vRw7j4w3tUh3-wlKUxXkTRuAp7cfIWA2SqTeIZXzsP9_YnybHwXb5krz3WWzFUPOWd_S7I5eDqORY5E/pub)
