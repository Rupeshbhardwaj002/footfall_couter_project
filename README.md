# footfall_couter_project
Footfall Counter using Computer Vision
 1. Approach
This project implements a footfall counter that detects and tracks people entering or exiting a specific region in a video using YOLOv8 and Centroid Tracking.
•	The YOLO model (pretrained on the COCO dataset) is used to detect persons in each frame.
•	Each detected person is assigned a unique ID using a centroid-based tracking algorithm.
•	A vertical ROI line is defined in the frame, and when tracked centroids cross this line, entry or exit events can be determined.
•	Bounding boxes and unique IDs are displayed for each person in real-time.
This system demonstrates understanding of AI model integration, tracking logic, and real-time visual analysis.
________________________________________
 2. Video Source Used
Publicly available YouTube videos and other platforms(PiXabay, etc) showing people moving through a corridor , street etc with a stable camera.
It was hard to find the video of our requirement that is why I also used a video of myself.
All videos 
________________________________________
3. Explanation of Counting Logic
1.	The YOLO model detects all persons (class=0) in each frame.
2.	Each bounding boxes centroid is computed and tracked across frames using a Centroid Tracker.
3.	A vertical line (ROI) is drawn in the center of the frame.
4.	When a person’s centroid crosses this ROI from left to right or right to eft, it is counted as an entry or exit.
5.	The counts are displayed on the video along with tracked IDs and bounding boxes.
(Note: Accuracy may slightly drop in overlapping or occlusion cases.)
________________________________________
4. Dependencies and Setup Instructions
Requirements:
•	Python ≥ 3.8
•	Google Colab or local environment with GPU recommended
Install dependencies:
pip install ultralytics opencv-python numpy
Run the notebook:
1.	Open footfall_counter.ipynb in Google Colab or Jupyter.
2.	Upload your input video (u can also check our output file where I have given the download link of our input videos u can also try them).
3.	Execute all cells in order.
4.	The processed video (output_video.mp4) will be generated with bounding boxes and tracking overlays.
5.	The output_video.mp4 can be directly downloaded or run -> flies.download(“content/output_video.mp4”)
5 Drawbacks
Our project is working fine for our sample 1 result where we have only one person(its me) only without any (overlapping) but fails in sample 2 result where at 0.3 seconds a cyclist and a girl both gets out at same time but our model assigns it only one. Same happens with sample 3 results.
Hence we have these all isssues -
Overlapping People issue
•	When two or more people pass very close together or overlap, the tracker may merge or lose identities.
•	This causes miscounting (ex- one person counted twice or missed entirely).
Dependence on Video Angle issue
•	The system performs best when the camera is positioned directly facing or above the ROI (doorway).
•	Side-angle or tilted footage can cause centroid detection errors, reducing accuracy.
•	The ROI (vertical line) is fixed. If the video frame or scene changes (camera moves or shakes), accuracy drops.
•	Dynamic or adaptive ROI positioning is not implemented.
Limited Real-Time Performance
•	Since YOLOv8 runs on CPU (if GPU not available), frame processing may be slower for real-time applications.
Counting Logic Simplification
•	The entry/exit counting logic assumes a clean left<->right or right<->left movement.
•	Complex paths (like diagonal or circular motion) may not be interpreted correctly.
