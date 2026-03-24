---
title: Raven Detection
emoji: 🚀
colorFrom: blue
colorTo: indigo
sdk: docker
pinned: false
---

<div align="center">
  <h1>RAVEN: Orientation-Aware Object Detection for Aerial Imagery</h1>
</div>

<p align="center">
  <a href="https://huggingface.co/spaces/Deepu61004/raven-detection">
    <img src="https://img.shields.io/badge/Demo-Hugging%20Face%20Spaces-blue?style=for-the-badge&logo=huggingface" alt="Hugging Face Deployment">
  </a>
  <img src="https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/YOLOv8-Ultralytics-0073F7?style=for-the-badge" alt="YOLOv8">
  <img src="https://img.shields.io/badge/Flask-Web%20App-000000?style=for-the-badge&logo=flask&logoColor=white" alt="Flask">
</p>

## 1. Abstract

**RAVEN (Rotated-Annotation Vehicle and Entity Network)** is a comprehensive deep learning application engineered for high-precision, orientation-aware object detection in aerial and satellite imagery. By extending the **YOLOv8-OBB (Oriented Bounding Boxes)** framework, RAVEN overcomes the limitations of standard horizontal bounding boxes, accurately resolving the spatial orientation of densely packed objects such as vehicles, aircraft, and maritime vessels.

The system features a production-ready Flask web interface providing user authentication, real-time inference visualization, centralized historical telemetry via a cloud database, and automated analytical reporting.

---

## 2. Core Capabilities

* **Multi-Modal Inference:** Supports dynamic switching between Standard YOLOv8, DOTA-OBB, and HRSC-OBB models to accommodate diverse aerial datasets.
* **Fine-Grained Classification:** Implements secondary inference pipelines utilizing the FAIR1M dataset for highly specific subset classification of detected objects.
* **Centralized Telemetry:** Inference metrics (object density, frames per second, processing latency) are aggregated and persisted across sessions using a global Clever Cloud MySQL database.
* **Automated Analytics:** Authorized users can export session data and visual outputs into structured CSV spreadsheets or comprehensive PDF documents.
* **Containerized Deployment:** Packaged via Docker for seamless portability and deployed as an interactive application on Hugging Face Spaces.

---

## 3. Technical Architecture

* **Computer Vision Backbone:** PyTorch, Ultralytics YOLOv8-OBB, OpenCV
* **Backend Infrastructure:** Python 3.12, Flask, Gunicorn, Werkzeug
* **Data Persistence:** PyMySQL (Clever Cloud MySQL instance)
* **Frontend Presentation:** HTML5, CSS3, Vanilla ES6 JavaScript
* **Reporting Engine:** ReportLab (PDF configuration), CSV Module
* **Version Control & CI/CD:** Git LFS, Docker

---

## 4. Installation & Deployment

### 4.1 Prerequisites
Due to the integration of proprietary Model Weights (`.pt` files) exceeding standard repository limits, **Git Large File Storage (LFS)** is mandatory prior to repository cloning.

* [Git LFS](https://git-lfs.com/)
* [Python 3.10+](https://www.python.org/downloads/)
* [Docker](https://www.docker.com/) (Optional, for containerized execution)

### 4.2 Local Environment Setup

**1. Clone the Repository:**
```bash
git lfs install
git clone https://github.com/AnudeepGonuguntla/orientation-aware-object-detection-yolov8.git
cd orientation-aware-object-detection-yolov8
```

**2. Initialize Virtual Environment:**
```bash
python -m venv venv
# Windows:
.\venv\Scripts\activate
# Linux/macOS:
source venv/bin/activate
```

**3. Install Dependencies:**
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

**4. Execute the Server:**
```bash
python app.py
```
The application will initialize at `http://127.0.0.1:5000`.

---

## 5. Cloud Configuration Options

The application relies on secure environment variables for production telemetry. For local development isolated from the Clever Cloud cluster, map the following variables in a `.env` file:
* `DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD`, `DB_NAME`
* `SECRET_KEY` (Cryptographic key for Flask session signing)

*(Note: In the absence of these variables, the application defaults to hardcoded fallback connections).*

---

## 6. Hugging Face Spaces Deployment

The repository is configured for native compliance with the Hugging Face Spaces Docker SDK.

1. Provision a New Space on [Hugging Face](https://huggingface.co/spaces) using the **Docker** > **Blank** template.
2. Link the Hugging Face remote to your local repository:
   ```bash
   git remote add huggingface https://huggingface.co/spaces/<USERNAME>/<SPACE_NAME>
   ```
3. Push via Git LFS using a valid Write-Access Token:
   ```bash
   git push -f huggingface main
   ```

---

## 7. License & Acknowledgements

Distributed under the MIT License. See `LICENSE` for more information.  
Special thanks to the [Ultralytics](https://github.com/ultralytics/ultralytics) team for the underlying YOLO architecture and the open-source DOTA/HRSC aerial dataset communities.
