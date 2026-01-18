# BuddyGuard - Anti-Ragging Violence Detection System
![banner](https://github.com/mohesh-coder/BuddyGuard/blob/a4d18595f9389a220094341c04a5512db8777f7d/asset/Banner.png)

**Real-time violence detection in campus videos using ConvLSTM — designed to support anti-ragging efforts in Indian colleges and universities.**

[![Python](https://img.shields.io/badge/Python-3.10%2B-blue)](https://www.python.org/)
[![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange)](https://www.tensorflow.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## Overview

This project implements a **Convolutional LSTM (ConvLSTM)** model for detecting violent activities in video sequences. It classifies frame sequences as **"Normal"** or **"Violence"** with ~91.8% accuracy (on the trained checkpoint provided).

**Primary intended application**: Enhancing **anti-ragging surveillance** in Indian educational institutions by analyzing live CCTV feeds or recorded footage in high-risk areas (hostels, corridors, canteens, orientation zones), enabling faster alerts and better documentation.

**Important note**: This is **not** a production-ready security system. It is an open-source prototype/research tool. Any real-world deployment must include human verification, strict privacy controls, institutional ethics approval, and compliance with Indian laws (UGC regulations, DPDP Act 2023).

## Problem It Addresses

Ragging remains a serious issue in many Indian colleges despite UGC regulations and Supreme Court guidelines (2009 onwards). Recent reports (2023–2025) show:

- Rising complaints and tragic outcomes (suicides, injuries)
- Low resolution rates and under-reporting
- Inadequate real-time monitoring even in CCTV-equipped campuses

Manual review of footage is slow and inefficient. An automated early-warning layer can help institutions respond faster while generating verifiable evidence.

## How It Works

1. **Input** → YouTube video, local file, or live webcam/CCTV feed  
2. **Preprocessing** → Resize frames to 64×64, normalize, maintain 20-frame sliding window  
3. **Model** → ConvLSTM processes spatio-temporal features → outputs probability of violence  
4. **Output** → Annotated video with overlaid label ("Violence" / "Normal") or live display + optional alert trigger

## Key Features

- Real-time / near real-time inference on live camera  
- YouTube video download & processing pipeline (via yt-dlp)  
- Sequence-based temporal modeling (20 frames) — better at detecting group aggression patterns  
- Annotated output videos for post-incident review  
- Modular code structure (easy to extend / fine-tune)  
- Configurable via YAML (sequence length, resolution, thresholds, etc.)

## Tech Stack

| Component          | Technology                  |
|--------------------|-----------------------------|
| Deep Learning      | TensorFlow / Keras          |
| Model Architecture | ConvLSTM (Conv2D + LSTM)    |
| Video Processing   | OpenCV                      |
| YouTube Download   | yt-dlp                      |
| Environment        | Python 3.10+                |
| Prototyping        | Jupyter Notebooks           |

## Folder Structure

```text
BuddyGuard/
├── notebooks/
│   ├── working.ipynb
│   └── noragproject.ipynb      # Main development & analysis
├── models/
│   └── convLSTM_*.h5           # Pre-trained weights
├── output_videos/              # Detection results
├── requirements.txt            # Environment dependencies
└── README.md
```

**Installation**
----------------
### 1️ Clone the Repository
python 
```
git clone https://github.com/yourusername/anti-ragging-violence-detection.git

cd anti-ragging-violence-detection
```
### 2️ Create a Virtual Environment
python 
```
python -m venv venv

source venv/bin/activate

# venv\Scripts\activate
```
### 3️ Install Dependencies
python 
```
pip install -r requirements.txt
```

Results Snapshot (from provided model)
--------------------------------------

-   Validation Accuracy: **91.8%**
    
-   Validation Loss: **0.234**
    
-   Strong at capturing motion patterns (pushing, grouping, sudden aggression)
    

→ See notebooks/noragproject.ipynb for loss curves, confusion matrix, and qualitative examples.

Ethical & Deployment Considerations
-----------------------------------

**This system is a prototype — not for autonomous action.**

Must-have safeguards before campus use:

-   Human-in-the-loop verification of every alert
    
-   Face anonymization / blurring in stored footage
    
-   Data retention policy (delete non-alert clips immediately)
    
-   Institutional ethics committee / IRB approval
    
-   Student consent & transparency (notices: "AI-monitored area for safety")
    
-   Compliance with UGC anti-ragging regs + DPDP Act 2023
    
-   Avoid over-surveillance perception — focus only on violence indicators
    

**Recommended pilot**: 2–4 cameras in one hostel block → alerts to warden/security via Telegram/WhatsApp.

Future Roadmap
--------------

-   Fine-tune on India-specific campus footage (sports vs. aggression differentiation)
    
-   Edge deployment (TensorFlow Lite + Raspberry Pi / Jetson Nano)
    
-   Multi-class expansion (verbal harassment proxies, group size estimation)
    
-   Alert integration (campus security dashboard, helpline escalation)
   
-   Collaboration with anti-ragging NGOs (SAVE, Coalition to Uproot Ragging)
    

License
-------

MIT License — feel free to fork, modify, and use (with attribution).
