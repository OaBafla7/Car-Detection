Vehicle Detection & Tracking Using OpenCV (Euclidean Distance Tracker)
This project uses OpenCV and a custom Euclidean distance-based tracker to detect and track moving vehicles in a video stream. It combines background subtraction and object filtering techniques to identify and follow cars across frames.

📽️ Overview
This Python script performs the following tasks:

Reads frames from a video file (vid.mp4)

Applies background subtraction using cv2.createBackgroundSubtractorMOG2

Filters detected moving objects by size and aspect ratio to focus on vehicles

Tracks vehicles using a Euclidean distance tracker, assigning unique IDs

Displays bounding boxes and IDs on the detected vehicles in real-time

🎯 Features
Accurate vehicle detection using background subtraction

Custom tracking algorithm using Euclidean distance

Filters out noise and small objects

Annotated frame display with object IDs

Simple and efficient design — no external ML models required

📂 Project Structure
bash
Copy
Edit
project/
│
├── vid.mp4               # Input video file (your traffic or surveillance video)
├── vehicle_tracker.py    # Main Python script
├── README.md             # This documentation file
🧠 How It Works
🔹 Detection
A Region of Interest (ROI) is extracted from the video to focus on a specific area.

Gaussian blur is applied to reduce noise.

Background subtraction isolates moving objects.

Morphological operations clean up the binary mask.

Bounding boxes are drawn for blobs that are likely vehicles (filtered by area and aspect ratio).

🔹 Tracking
The tracker assigns a unique ID to each object.

It compares the current positions of objects with previously stored positions.

If the distance between centers is within a threshold, the same ID is maintained.

New objects are assigned new IDs.

🛠️ Requirements
Make sure you have the following installed:

bash
Copy
Edit
pip install opencv-python numpy
▶️ How to Run
Replace vid.mp4 with your own traffic or surveillance video.

Run the script:

bash
Copy
Edit
python vehicle_tracker.py
Press ESC to exit the video window.

⚙️ Customization
Region of Interest:

python
Copy
Edit
roi = frame[340:720, 500:800]
Adjust these values to match the area of interest in your video.

Detection Thresholds:

area > 100: Filter small movements

0.5 < aspect_ratio < 3.0: Filter non-vehicle shapes

w > 30 and h > 30: Ensure reasonable object size

Tracking Distance:

python
Copy
Edit
self.max_distance = 50
Increase this value for faster-moving vehicles or noisy detections.

🖼️ Output
The following windows will be displayed:

ROI: The selected detection area with bounding boxes and IDs

Frame: The full original frame

Mask: The binary foreground mask used for detection

📦 Future Improvements
Integrate with YOLO or a deep learning model for better classification

Add line crossing logic to count vehicles

Export tracking data to CSV for analysis

