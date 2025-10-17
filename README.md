# // SYNTHESIS-OS: Digital Identity Synthesis Engine

> SYSTEM INITIATED. CORE PROTOCOL ONLINE. ACCESS LEVEL: OPERATOR.

**SYNTHESIS-OS** is a specialized, single-screen web application designed to generate stylized, high-fidelity character portraits from user-provided reference photos. It transforms the process of AI-powered image generation into an immersive, retro-hacker terminal experience, complete with bespoke UI elements and system logs.

The goal is to provide a unified, highly stylized interface for **advanced identity mapping and diffusion model prompting**.

## ⚙️ Core Functionality & Architecture

The application is structured into three main layers: the UI/Client, the API/Backend, and the AI Core, which work together to handle the complex generation workflow.

### 1. The Input & Mapping Protocol (CV)

The system is designed to accept multiple reference images (front, left profile, right profile).

* **Facial Feature Preservation:** Utilizes Computer Vision libraries (like **OpenCV** or **Face-api.js**) to detect and map key facial landmarks.
* **ControlNet Integration:** The mapped data is converted into control maps (e.g., Canny edges or OpenPose) for the AI Core, ensuring the generated output retains the core identity and pose of the input subject, regardless of the prompt style.

### 2. The Command Console (UI)

The user interacts with a persistent, single-screen interface crafted in a strict **CRT/retro-terminal style**.

* **Single-Pane View:** All controls, inputs, logs, and outputs are presented on one screen, mimicking a dedicated system console.
* **Aesthetic Styling:** Employs **monospaced fonts (e.g., VT323)**, neon color palettes (e.g., cyan, amber), and CSS effects (scanlines, text flicker) for a genuine 80s computer feel.
* **System Log:** A dedicated, scrolling text area provides real-time feedback on API status, processing times, and generation queue updates.

### 3. Identity Synthesis (AI Core)

This is the engine where the final characters are rendered.

* **Generative AI Backbone:** The core uses a large **Text-to-Image Diffusion Model** (e.g., a self-hosted Stable Diffusion instance or a robust cloud API like Stability AI or Midjourney).
* **Parameter Assembly:** The user's text prompt, style presets, and identity control maps are merged into a single, optimized payload before execution.

## 🛠️ Technology Stack

| Layer | Primary Technology | Rationale |
| :--- | :--- | :--- |
| **Frontend** | **React** (or Vue/Svelte) | For robust, component-based state management, crucial for a complex, single-screen application. |
| **Styling** | **SCSS/CSS Modules** | To manage the highly customized and detailed retro visual effects (scanlines, flicker, custom borders). |
| **Backend API** | **Python (FastAPI/Flask)** | Excellent ecosystem for handling high-load AI processing tasks and managing external generative model APIs. |
| **CV/Mapping** | **OpenCV** & Python Libraries | For rapid, accurate facial landmark detection and preparing ControlNet maps. |
| **AI/ML** | **ControlNet** & **Diffusion Model API** | ControlNet is essential for ensuring identity and pose consistency across different generated styles. |
| **Database** | **Redis** (or similar) | Used for caching generation results and managing the unique project hash/name generation process. |

## 🚀 Getting Started (Operator Guide)

To run the **SYNTHESIS-OS** locally, you will need Node.js, Python 3.9+, and access to a generative AI API (or a running local model instance).

### Prerequisite Setup

1.  **Clone Repository:**
    ```bash
    git clone [https://github.com/makalin/synthesis-os.git](https://github.com/makalin/synthesis-os.git)
    cd synthesis-os
    ```
2.  **Environment Variables:** Create a `.env` file in the root directory and populate it with your API keys and configuration settings:
    ```
    # Example: Stability AI or other API key
    AI_API_KEY="YOUR_GENERATIVE_AI_API_KEY" 
    BACKEND_PORT=8000
    FRONTEND_PORT=3000
    ```

### Frontend Initialization

```bash
# Navigate to the client directory
cd client 
npm install
npm run dev
# Front-end Console initialized on: http://localhost:3000
````

### Backend Server Deployment

```bash
# Navigate back to the root and into the server directory
cd ../server
pip install -r requirements.txt
python main.py
# Backend Protocol established on: http://localhost:8000
```

## 📜 Directive Log

The system automatically generates a unique, traceable **Project Hash** for every synthesis session to ensure versioning and retrieval of generated assets.

> **Example Log:** `// [2025-10-17 14:50:15] QUERY PARSED: "Neo-noir detective in the rain" // IDENTITY MATRIX: LOADED from makalin_ref_01.jpg // CONTROL SIGNAL: CONTROLNET-POSE-STRONG // STATUS: EXECUTION COMMENCED // PROJECT HASH: #A9B3E-2025-ALPHA`
