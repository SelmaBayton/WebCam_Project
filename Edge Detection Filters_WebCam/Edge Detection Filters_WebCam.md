# Image Filtering Web Application

This Python code implements a web application that captures a frame from the webcam, applies different image filters using convolution, and displays the filtered images in a grid layout.

## Prerequisites

- Python 3.x
- OpenCV library (`cv2`)
- Pillow library (`PIL`)
- NumPy library (`numpy`)
- Microdot library (`microdot`)
- SciPy library (`scipy`)
- Base64 library (`base64`)

## Installation

1. Install Python 3.x from the official Python website: https://www.python.org/downloads/
2. Install the required libraries by running the following command:
   ```
   pip install opencv-python pillow numpy microdot scipy
   ```

## Usage

1. Connect a webcam to your computer.
2. Run the Python script `app.py`.
3. The web application will start and display a grid of filtered images.
4. Each image in the grid represents a different image filter.
5. The original captured frame is converted to grayscale.
6. The grayscale image is then convolved with different kernels to apply the image filters.
7. The filtered images are displayed in a grid layout on the web page.
8. Access the web application through the provided URL (e.g., http://localhost:8008) in a web browser.
9. The web page will show the filtered images.

## Code Explanation

### Image Filtering

1. Import the necessary modules: `cv2`, `Image` from `PIL`, `numpy`, `Microdot`, `signal` from `scipy`, `base64` from `io`.
2. Define a dictionary `kernels` that contains different image filter kernels.
3. Define a function `apply_kernel(img, kernel)` to apply a kernel convolution to an image.
   - Use `signal.convolve2d` from `scipy` to convolve the image with the given kernel.
   - Clip the convolved values to ensure they are within the valid range for `uint8`.
   - Convert the convolved array back to a `PIL` image and return it.

### Data URL Conversion

1. Define a function `image_to_data_url(img)` to convert an image to a data URL.
   - Create a buffered object using `BytesIO`.
   - Save the image to the buffered object as a JPEG format.
   - Encode the buffered value as a base64 string and prepend the appropriate data URL prefix.
   - Return the data URL string.

### Web Application Route

1. Create a `Microdot` application instance.
2. Set the default content type of the response to `text/html`.
3. Define the route `/` and the corresponding handler function `index(request)`.
   - Initialize the webcam using `cv2.VideoCapture(0)`.
   - Check if the webcam is opened successfully. If not, return an error message.
   - Capture a single frame from the webcam.
   - Release the webcam.
   - Check if the frame is received successfully. If not, return an error message.
   - Convert the frame to grayscale using `cv2.cvtColor()`.
   - Convert the grayscale image to a `PIL` image.
   - Apply each kernel from the `kernels` dictionary to the grayscale image using the `apply_kernel()` function and store the results in `kernel_images`.
   - Generate HTML elements for each filtered image, including the image name and its corresponding data URL.
   - Build the HTML content by concatenating the HTML elements.
   - Return the HTML content as the response.

### Running the Application

1. Check if the script is being run directly by checking if `__name__ == "__

main__"`.
2. Start the `Microdot` application by calling `app.run()` with the appropriate options.


