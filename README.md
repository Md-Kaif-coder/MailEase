# ✉️ MailEase

### AI-Powered Email Reply Assistant

MailEase is an AI-powered email reply assistant that helps users generate clear, professional, and context-aware email responses in seconds.

It combines a **React frontend**, **Spring Boot backend**, **Google Gemini API**, and a browser extension to simplify the process of writing email replies.

---

## 🚀 Overview

Writing professional email replies can often be repetitive and time-consuming.

MailEase solves this problem by allowing users to:

- Paste an email or email content
- Select the desired communication tone
- Generate an AI-powered reply
- Review the generated response
- Copy the response with a single click

The application is designed with a separate frontend and backend architecture, making it easier to maintain, extend, and integrate with other platforms in the future.

---

## ✨ Features

- 🤖 **AI-Powered Reply Generation**
  - Generates email replies using Google Gemini.

- 🎯 **Tone Selection**
  - Professional
  - Casual
  - Friendly

- 🧠 **Context-Aware Responses**
  - Uses the original email content as context while generating the reply.

- ✍️ **Professional Prompt Engineering**
  - Designed to avoid unnecessary details, fake information, placeholders, and subject lines.

- 📋 **One-Click Copy**
  - Easily copy the generated reply to the clipboard.

- 🌐 **React Web Interface**
  - Clean and simple interface for interacting with the application.

- ⚡ **Spring Boot REST API**
  - Backend API handles requests and communicates with the Gemini API.

- 🧩 **Browser Extension**
  - Extension-based integration is included as part of the project structure.

---

## 🏗️ System Architecture

```mermaid
flowchart TD

    A[User] --> B[MailEase Web Interface]
    A --> C[MailEase Browser Extension]

    B --> D[Spring Boot REST API]
    C --> D

    D --> E[EmailGeneratorController]
    E --> F[EmailGeneratorService]

    F --> G[Google Gemini API]

    G --> F
    F --> D
    D --> B

    B --> H[Generated Email Reply]



    Request Flow
User
  │
  ▼
React / Browser Extension
  │
  │ POST /api/email/generate
  ▼
Spring Boot Controller
  │
  ▼
Email Generator Service
  │
  ▼
Google Gemini API
  │
  ▼
Generated Email Reply
  │
  ▼
Frontend
🛠️ Tech Stack
Frontend
React
Vite
JavaScript
HTML
CSS
Backend
Java
Spring Boot
Spring Web
Spring WebFlux
REST API
Maven
Lombok
AI
Google Gemini API
Prompt Engineering
Browser Integration
Browser Extension
Development Tools
IntelliJ IDEA
Visual Studio Code
Git
GitHub
Maven
📁 Project Structure
MailEase/
│
├── email-writer-ext/
│   └── Browser extension implementation
│
├── email-writer-react/
│   └── React + Vite frontend
│
├── email-writer-sb/
│   └── Spring Boot backend
│
├── hello-world-ext/
│   └── Extension development/testing module
│
├── email-writer-sb.zip
│   └── Backend project archive
│
└── README.md
🔄 How MailEase Works
1. Enter Email Content

The user provides the original email content through the MailEase interface.

2. Select Tone

The user can select the desired response tone:

Professional
Casual
Friendly
3. Generate Reply

The frontend sends the request to the Spring Boot backend.

4. Backend Processing

The Spring Boot application receives the request through a REST endpoint and passes the email content to the email generation service.

5. AI Processing

The backend creates a structured prompt and sends it to the Google Gemini API.

6. Response Processing

The generated response is extracted from the Gemini API response.

7. Display & Copy

The generated email reply is returned to the frontend, where the user can review and copy it.

🔌 API Documentation
Generate Email Reply

Endpoint

POST /api/email/generate
Request
{
  "emailContent": "Hi Kaif, Could you please share the latest project update?",
  "tone": "professional"
}
Response
Thank you for reaching out. I would be happy to provide
an update on the project.
Supported Tone Examples
professional
casual
friendly
⚙️ Backend Configuration

The Gemini API configuration is kept outside the source code using environment variables.

Environment Variables
GEMINI_URL
GEMINI_KEY

The Spring Boot application reads these values through:

gemini.api.url=${GEMINI_URL}
gemini.api.key=${GEMINI_KEY}
Why Environment Variables?

API credentials should never be hard-coded or committed to a public repository.

This keeps sensitive configuration separate from the application source code.

🧪 Example
Input
Hi Kaif,


I wanted to follow up regarding the project update.
Could you please share the current status?


Thanks,
Rahul
Tone
Professional
Generated Reply
Hi Rahul,


Thank you for reaching out regarding the project update.
I will be happy to provide the current status and keep
you informed of any relevant developments.


Best regards,
Kaif
🖥️ Application
Web Interface

The MailEase web interface provides:

Original email input
Tone selection
Reply generation
Generated response display
Copy-to-clipboard functionality

Screenshots and demo GIFs can be added here as the project evolves.

🔐 Security Considerations

MailEase keeps the Gemini API key outside the source code using environment variables.

Source Code
    │
    ├── Application Logic
    ├── API Configuration
    │
    └── No API Secret
             │
             ▼
       Environment Variables
