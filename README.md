# 🛡️ Dangerous Object Detection with Email Alerts

This project uses **YOLOv8**, **Ultralytics**, and **Supervision** to detect dangerous objects in a video stream and send automatic email alerts when one is found.

---

## 🔍 Features

- 🚨 Real-time detection of dangerous objects (e.g., knife, gun, scissors)
- 📬 Email alerts when a threat is detected
- 🧠 Uses YOLOv8 (`yolov8n.pt`) from Ultralytics
- 🔁 Skips frames to optimize processing
- ✅ Easy customization of detection threshold and alert logic

---

## 🧠 Requirements

- GPU runtime recommended (e.g., Google Colab with GPU)
- Python 3.11+

**Install dependencies**:
```bash
pip install ultralytics roboflow supervision opencv-python numpy
```

## 🧪 How to Run
1. Clone or open the notebook in your preferred environment (e.g., Google Colab).
2. Update the video path to point to your test video (sample available):
```bash
https://drive.google.com/file/d/1GjJA5tb-jRh4OTBnm_nLqs2xuNKk6vdh/view?usp=sharing
```

Example in code:

```bash
cap = cv2.VideoCapture("/path/to/video.mp4")
```

3. Configure the send_alert function:
  - Update your sender email, password (app-specific), and recipient email inside the send_alert() method:
    
```bash
sender_email = "youremail@gmail.com"
sender_password = "your-app-password"
receiver_email = "receiveremail@gmail.com"
```

4. (Optional) Adjust detection confidence:
   
```bash
results = model(frame, conf=0.6)[0]  # You can increase or decrease the threshold
```

## ⚠️ Alert Logic
- Alerts are sent only once per object (first detection).
- You can modify this logic to resend alerts every N detections if desired.

## 🎯 Dangerous Object Classes
The following classes are considered dangerous by default:
```bash
dangerous_objects = ['knife', 'scissors', 'gun']
```

## 📬 Sample Alert Email
```bash
Subject: ALERT: Dangerous Object Detected!

SECURITY ALERT

Object detected: knife  
Confidence: 98.42%  
Timestamp: 2025-04-09 15:27:45  
```
