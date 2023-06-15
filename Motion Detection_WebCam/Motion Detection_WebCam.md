# Webcam Motion Detection

This Python code implements a motion detection system using a webcam. When motion is detected, it captures a frame and saves it as an image file.

## Prerequisites

- Python 3.x
- OpenCV library (`cv2`)

## Installation

1. Install Python 3.x from the official Python website: https://www.python.org/downloads/
2. Install the OpenCV library by running the following command:
   ```
   pip install opencv-python
   ```

## Usage

1. Connect a webcam to your computer.
2. Run the Python script `motion_detection.py`.
3. The script will start capturing frames from the webcam and perform motion detection.
4. When motion is detected, it will save the captured frame as an image file.
5. Press 'q' to stop the motion detection and exit the script.

## Code Explanation

### Motion Detection

1. Import the necessary modules: `cv2` and `os`.
2. Initialize the webcam using `cv2.VideoCapture(0)`.
3. Define a global variable `motion_detected` to track motion detection.
4. Define a function `capture_motion()` to capture a frame when motion is detected.
   - Check if motion was detected.
   - If motion was detected, capture a single frame from the webcam.
   - Generate a unique filename based on the current timestamp.
   - Save the frame as an image file with the generated filename.
   - Print a message indicating the motion detection and the saved image filename.
   - Reset the motion detection flag.
5. Define a function `motion_detection()` to perform motion detection continuously.
   - Set up motion detection parameters, such as the motion threshold.
   - Read the first frame for motion detection.
   - Convert the frame to grayscale and apply Gaussian blur.
   - Start an infinite loop to continuously read frames from the webcam.
   - Convert the current frame to grayscale and apply Gaussian blur.
   - Calculate the absolute difference between the current and previous frames.
   - Apply thresholding to highlight the differences.
   - Calculate the total number of non-zero pixels in the threshold image.
   - If the number of motion pixels exceeds the threshold, set the `motion_detected` flag to True.
   - Update the previous frame for the next iteration.
   - Call the `capture_motion()` function if motion is detected.
   - Wait for a key press and exit the loop if 'q' is pressed.
6. Check if the script is being run directly by checking if `__name__ == '__main__'`.
7. Start the motion detection by calling the `motion_detection()` function.
