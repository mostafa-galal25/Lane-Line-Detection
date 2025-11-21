🚧# Real-Time Lane Line Detection

A computer vision project implementing a standard pipeline to detect and draw lane lines on static images and in real-time video streams using OpenCV and Numpy.
This project is a classic demonstration of combining image processing and geometric algorithms for self-driving applications.

#🌟 Features

Robust Processing Pipeline:Implements a full lane line detection pipeline:
Grayscale & Blur: Converts the image to grayscale and applies Gaussian blur to reduce noise. 
Edge Detection: Uses the Canny Edge Detector to find strong intensity gradients (edges).
Region of Interest (ROI) Masking: Masks the image to focus processing only on the relevant area of the road.
Line Detection: Applies the Hough Transform (HoughLinesP) to identify straight line segments.
Lane Formulation: Contains helper functions to average and extend the detected line segments into two solid, definitive lane lines (left and right).
Real-Time Video Analysis: Processes video files frame-by-frame, applying the detection pipeline continuously.
Interactive Testing: Includes a segment using OpenCV Trackbars for interactively adjusting Canny edge detection thresholds (x, y, x2, y2) to visualize the impact on edge quality.
Output Visualization: Overlays the detected lane lines (colored Orange/Red) onto the original image/video frame using cv2.addWeighted() for a clear visual result.

#🛠️ Technologies Used

Technology  Purpose
Python      Core programming language.
OpenCV  (cv2)Image processing, edge detection, Hough Transform, video reading, and visualization.
NumPy  Array manipulation, defining the ROI polygon, and calculating line averages.
math   Essential for slope and intercept calculations in the lane formulation function.

#📦 Prerequisites and Setup

Before running the project, ensure you have the necessary libraries installed:
pip install opencv-python numpy matplotlib


#📂 File Structure Note (Crucial for Portability)

Your code currently uses absolute file paths (e.g., "C://Users//HP//Downloads//solidWhiteCurve (1).jpg").
For this project to work on GitHub, you must:Create a data folder in your project root.
Place all necessary images and video files (e.g., solidWhiteCurve.jpg, solidYellowCurve2.jpg, solidWhiteRight.mp4) inside this data folder.
Update the paths in your Python code to use relative paths like "data/solidWhiteCurve.jpg" or "data/solidWhiteRight.mp4".

#▶️ How to Run

The project is structured within a Jupyter Notebook, which allows for step-by-step execution.

1. Interactive Canny Edge Testing (Cells 1-3)
  1. This section lets you experiment with the Canny algorithm's sensitivity:
  2. Run the code in the first few cells.
  3. Adjust the trackbars (x, y for Canny min/max thresholds) to see how the edge images change in real-time.
  4. Press 'q' to close the interactive windows.
2. Static Image Lane Detection (Cells 4-7)
  This section applies the full pipeline to static images:
 1. Ensure the helper functions (Cell 4) are defined.
 2. Run the subsequent cells to see the final output for the two test images (solidWhiteCurve and solidYellowCurve2) with the lane lines drawn.
 3. Press 'q' to close the windows.
3. Real-Time Video Lane Detection (Cell 8)
 This is the main demonstration of the project:
  1.Ensure you have placed the video file (solidWhiteRight.mp4) in the correct location (e.g., ./data/).
  2. Run the final cell.
  3. The output window will display the video with the lane lines detected and drawn in every frame.
  4. Press 'q' to stop the video playback.
    
#🧠 Pipeline Breakdown (Helper Functions)

The logic for extracting robust lane lines is contained in the helper functions:
helpers_edges(gray)  Canny Edge   DetectionApplies Gaussian Blur, then uses Canny with fixed thresholds (50, 150) to find edges.
helpers_masked_edges(edges)  Region of Interest (ROI)  Creates a trapezoidal mask to only keep edge pixels within the main driving area, ignoring the sky and distant objects.
helpers_hough_lines(img)  Probabilistic Hough Transform  Detects preliminary line segments in the masked image using parameters like RHO, THETA, and MIN_VOTES.
helpers_formulate_lanes(lines, img)  Averaging and Extrapolation  Filters line segments based on slope (positive for right, negative for left), calculates the mean slope and intercept for each lane, and extrapolates these two averaged lines back onto the ROI, resulting in clean, singular lane markers.helpers_draw_lines(lines, masked_edges)VisualizationDraws the final averaged lines onto a blank canvas that is then overlaid onto the original frame.

#🤝 Contributing

This project is a great starting point for advanced computer vision techniques.
Contributions are encouraged!
Potential areas for improvement include:
Implementing a Kalman Filter for smoother line transitions in the video.
Using more advanced techniques like HLS color space filtering for better detection under varied lighting.
Integrating a method to output the steering angle.
Please feel free to fork the repository, make improvements, and submit a Pull Request.

#📄 License

Distributed under the MIT License. See LICENSE for more information.
