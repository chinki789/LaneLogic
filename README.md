🚦 LaneLogic

AI-Based Smart Traffic & Road Obstruction Analysis System

LaneLogic is an AI-based road obstruction and traffic analysis system developed for Smart India Hackathon 2026. It processes road/CCTV video to detect vehicles, track movement, identify obstruction events, analyze road-space usage, detect recurring issues, and generate actionable recommendations.

📌 Problem Statement

Urban roads lose usable space due to:

Vehicles stopping or parking on active lanes
Traffic congestion and signal queues
Loading/unloading activities
School drop-offs
Recurring road obstructions
Limited automated road monitoring

LaneLogic intelligently analyzes movement, duration, location, and traffic conditions before classifying an obstruction.

💡 Proposed Solution (Pipeline)
Traffic Video / Camera
        ↓
YOLOv8 Detection
        ↓
ByteTrack Tracking
        ↓
Vehicle Tracks
        ↓
Obstruction Events
        ↓
Road-Space + Severity + Cause Analysis
        ↓
Backend (FastAPI + Database)
        ↓
Recurrence Analysis + Recommendations
        ↓
Feedback / Alerts
🧠 AI & Computer Vision

Current Stack:

YOLOv8s (Detection)
ByteTrack (Tracking)
OpenCV

Parameters:

Image size: 640
Confidence: 0.40
IoU: 0.50

Vehicle Classes (COCO):

Car, Motorcycle, Bicycle, Bus, Truck

Upcoming Custom Dataset (10 classes):

Car, Motorcycle, Bicycle, Auto-rickshaw, E-rickshaw, Bus, Truck, Stall, Garbage, Scooty
⚙️ System Modules
👤 Person 1 — Detection & Obstruction Events
YOLO detection & ByteTrack tracking
Vehicle classification & tracking IDs
Movement vs stationary detection
Time-based obstruction detection
Event generation
👤 Person 2 — Road-Space, Severity & Cause Analysis
Vehicle count and type analysis
Occupancy & blocked space calculation
Severity estimation
Rule-based cause classification

Analysis Window: 2 seconds

Cause Types:

traffic_signal_queue
loading_unloading
school_dropoff
illegal_parking
general_congestion
normal / unclassified
🔁 Recurrence Analysis
Identifies:
Isolated events
Recurring patterns
Location-specific issues
Time-based patterns
Chronic problem zones
🧾 Recommendation Engine

Pipeline:

Problem → Evidence → Cause → Interventions → Scoring → Recommendation
Based on road-space loss, recurrence, and confidence
Recommendations are suggestive, not guaranteed outcomes
🖥️ Backend

Built with:

FastAPI
SQLAlchemy
Pydantic
SQLite

Database:

sqlite:///./lanelogic.db

Supports:

Detections, events, analysis
Chronic zones
Recommendations
Feedback & alerts
Simulations & outcomes
🔄 Closed-Loop Architecture
Detection → Event → Cause Analysis → Recommendation → Authority Action → Outcome → Feedback → Learning
🛠️ Technologies Used
AI / Computer Vision
Python
YOLOv8 (Ultralytics)
OpenCV
ByteTrack
Backend
FastAPI
SQLAlchemy
Pydantic
SQLite
Development
Git, GitHub
VS Code
Pytest
📁 Project Structure
LaneLogic/
├── person1_detection/
├── person2_analysis/
├── person3_backend/
├── person4_recommendation/
├── core/
│   ├── event_engine.py
│   ├── generate_events.py
│   ├── geometry.py
│   ├── cause_classifier.py
│   ├── recurrence.py
│   ├── interventions.py
│   ├── outcomes.py
│   ├── simulation.py
│   ├── alerts.py
│   └── continuous_learning.py
├── tests/
├── run_closed_loop.py
├── start_backend.py
└── README.md
⚡ Installation
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd LaneLogic
venv\Scripts\activate

pip install -r person1_detection/requirements.txt
pip install -r person2_analysis/requirements.txt
pip install -r person3_backend/requirements.txt
pip install -r person4_recommendation/requirements.txt
▶️ Running the Project
Start Backend
python start_backend.py
Generate Events
python core/generate_events.py \
--input person1_detection/output/detections.json \
--roi person2_analysis/roi_config.json \
--api http://localhost:8000
Run Recommendation Engine
python person4_recommendation/main.py --api http://localhost:8000
Run Full Closed Loop
python run_closed_loop.py \
--input person1_detection/output/detections.json \
--roi person2_analysis/roi_config.json \
--api http://localhost:8000
Run Tests
pytest tests/
🚀 Enhancement Roadmap
Core Intelligence
Improved road-space measurement
Better cause classification
Explainable recommendations
Decision Support
Severity & confidence scoring
Human feedback integration
Before/after impact analysis
Operations
Real-time monitoring
Alerts system
Continuous learning
📊 Current Status
Detection & tracking: ✅
Analysis modules: ✅
Backend: ✅
Recommendation system: ✅
Closed-loop pipeline: ✅
Custom model training: 🔄 Planned
🏁 Project Info
Event: Smart India Hackathon 2026
Domain: Smart Traffic / Intelligent Transportation
Status: Active Development
