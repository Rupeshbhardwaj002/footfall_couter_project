# 👣 Footfall Counter using Computer Vision

## 1. Approach
This project implements a **Footfall Counter** that detects and tracks people entering or exiting a specific region in a video using **YOLOv8** and **Centroid Tracking**.

- The **YOLO model** (pretrained on the COCO dataset) is used to detect persons in each frame.  
- Each detected person is assigned a **unique ID** using a centroid-based tracking algorithm.  
- A **vertical ROI line** is defined in the frame, and when tracked centroids cross this line, **entry or exit events** can be determined.  
- **Bounding boxes and unique IDs** are displayed for each person in real-time.  

This system demonstrates understanding of **AI model integration, tracking logic, and real-time visual analysis.**

---

## 2. Video Source Used
Publicly available **YouTube videos** and **Pixabay** clips showing people moving through corridors, streets, etc., with a stable camera.  
It was hard to find videos matching our exact requirement, so a **self-recorded video** was also used.

🎥 All videos used are provided or linked in the output files.

---

## 3. Explanation of Counting Logic
1. The YOLO model detects all persons (`class=0`) in each frame.  
2. Each bounding box’s **centroid** is computed and tracked across frames using a **Centroid Tracker**.  
3. A **vertical line (ROI)** is drawn in the center of the frame.  
4. When a person’s centroid crosses this ROI line from **left to right** or **right to left**, it is counted as an **entry** or **exit**.  
5. The counts are displayed on the video along with tracked IDs and bounding boxes.  

> ⚠️ *Note: Accuracy may slightly drop in overlapping or occlusion cases.*

---

## 4. Dependencies and Setup Instructions

### Requirements
- Python ≥ 3.8  
- Google Colab or local environment (GPU recommended)

### Installation
```bash
pip install ultralytics opencv-python numpy 
``` 
### Run the notebook:
1.	Open footfall_counter.ipynb in Google Colab or Jupyter.
2.	Upload your input video (u can also check our output file where I have given the download link of our input videos u can also try them).
3.	Execute all cells in order.
4.	The processed video (output_video.mp4) will be generated with bounding boxes and tracking overlays.
5.	The output_video.mp4 can be directly downloaded or run -> flies.download(“content/output_video.mp4”)

