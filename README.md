---
title: Raven Detection
emoji: 🚀
colorFrom: blue
colorTo: indigo
sdk: docker
pinned: false
---

# 🦅 RAVEN: Orientation-Aware Object Detection for Aerial Imagery

**RAVEN (Rotated-Annotation Vehicle and Entity Network)** is a full-stack deep learning application built to detect rotated/oriented objects in aerial and satellite imagery. By leveraging an enhanced **YOLOv8-OBB** (Oriented Bounding Boxes) framework, the system accurately detects objects at any angle, making it ideal for satellite maps, drones, and aerial reconnaissance.

It features a complete **Flask web interface** with user authentication, real-time visualization, cloud database history tracking, and downloadable PDF/CSV reports.

### 🌐 Live Demo
**[Try RAVEN Live on Hugging Face Spaces](https://huggingface.co/spaces/Deepu61004/raven-detection)**

---

## ✨ Key Features
* **Orientation-Aware Detection (OBB):** Identifies objects like ships, vehicles, and planes at exact angles using the DOTA and HRSC datasets.
* **Multiple AI Models:** Choose between Standard YOLOv8, DOTA-OBB, HRSC-OBB, and Fine-Grained Classification models.
* **User Authentication:** Secure `bcrypt` hashed login and registration system.
* **Persistent History:** All detection statistics (Inference Time, FPS, Object Density) are tracked globally via a Clever Cloud MySQL database.
* **Advanced Reporting:** Export detailed detection analytics instantly as beautifully formatted **PDFs** or **CSV** spreadsheets.
* **Hugging Face Optimized:** Fully containerized via Docker and configured for iframe deployment on Hugging Face Spaces.

---

## 🛠️ Tech Stack
* **Deep Learning:** Python, PyTorch, YOLOv8 (Ultralytics), OpenCV
* **Backend:** Flask, Gunicorn
* **Database:** MySQL (PyMySQL), Clever Cloud
* **Frontend:** HTML5, CSS3, Vanilla JavaScript
* **Deployment:** Docker, Git LFS, Hugging Face Spaces

---

## 🚀 How to Run Locally

Because this project utilizes large `.pt` AI models, you must have **[Git LFS (Large File Storage)](https://git-lfs.com/)** installed on your machine before downloading the code.

### 1. Clone the Repository
```bash
git lfs install
git clone https://github.com/AnudeepGonuguntla/orientation-aware-object-detection-yolov8.git
cd orientation-aware-object-detection-yolov8
```

### 2. Install Dependencies
It is highly recommended to use a virtual environment.
```bash
# Create and activate a virtual environment (Windows)
python -m venv venv
.\venv\Scripts\activate

# Install the minimal required packages
pip install -r requirements.txt
```

### 3. Set Up Environment Variables (Optional)
By default, the application connects to the cloud database. If you want to use a local MySQL database, set the following environment variables or create a `.env` file:
* `DB_HOST`, `DB_PORT`, `DB_USER`, `DB_PASSWORD`, `DB_NAME`
* `SECRET_KEY` (Flask session key)

### 4. Run the Application
```bash
python app.py
```
Once the server starts, open your web browser and navigate to `http://127.0.0.1:5000`

---

## ☁️ Hugging Face Deployment

This project is built to run effortlessly on Hugging Face Spaces using the included `Dockerfile`.

1. Go to Hugging Face and create a new **Docker** Space.
2. Link your GitHub repository or use the Hugging Face CLI to add the huggingface remote:
   ```bash
   git remote add huggingface https://huggingface.co/spaces/YOUR_USERNAME/YOUR_SPACE_NAME
   git push -f huggingface main
   ```
*(Note: Ensure you generate a Hugging Face 'Write' Access Token to use as your password during the push!)*

---

## 🔮 Future Scope
* Integration of real-time drone RTSP video feeds.
* Advanced analytics dashboard for detecting traffic density patterns over time.
* Further optimization of model weights using TensorRT or ONNX for edge devices.
