<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
<body>

<h1>Wisconsin Autonomous Perception Coding Challenge</h1>

<p>This repository contains my submission for the Wisconsin Autonomous Perception Coding Challenge. The challenge is designed to evaluate my problem-solving approach in computer vision, with a focus on using OpenCV to detect the boundaries of a path defined by cones in an image.</p>

<h2>Solution Overview</h2>

<h3>Methodology</h3>
<ol>
    <li><strong>Preprocessing the Image:</strong> 
        <p>First, I converted the image to grayscale to simplify the data for boundary detection. Then, I applied Gaussian Blur to reduce noise and improve edge detection.</p>
    </li>
    <li><strong>Edge Detection:</strong>
        <p>I used the Canny Edge Detection method to detect edges in the image. This helps in identifying cone edges and path boundaries.</p>
    </li>
    <li><strong>Color Thresholding:</strong>
        <p>I applied color thresholding to isolate the cones from the rest of the image. This helps differentiate the cones from the background.</p>
    </li>
    <li><strong>Hough Line Transformation:</strong>
        <p>I used the Hough Line Transformation to detect the straight lines that represent the path's boundary based on the detected edges.</p>
    </li>
    <li><strong>Drawing Boundary Lines:</strong>
        <p>After detecting the lines, I drew them on the original image and saved it as <code>answer.png</code>.</p>
    </li>
    <li><strong>Clustering:</strong>
        <p>By using clustering techniques (e.g., K-means), I grouped the detected cones to identify the left and right boundaries of the path.</p>
    </li>
</ol>

<h3>What Worked Well</h3>
<p>The Canny edge detection worked effectively in highlighting the edges of cones. Hough Line Transformation provided accurate detection of straight boundary lines on the path.</p>

<h3>Challenges & What Didn't Work</h3>
<ul>
    <li><strong>Challenge with Cone Detection:</strong> Initially, using only edge detection caused too much noise from other objects. This was mitigated by using color thresholding to isolate the cones based on their color.</li>
    <li><strong>Shadows and Lighting Variability:</strong> Variations in lighting conditions made it difficult to consistently detect cones. To address this, I fine-tuned the thresholding values and applied histogram equalization to balance the lighting.</li>
</ul>

<h2>Result</h2>

<p>The algorithm successfully detected and marked the boundaries of the path, as shown in <code>answer.png</code>:</p>

<img src="answer.png" alt="answer.png" width="500px">

<h2>Libraries Used</h2>
<ul>
    <li><strong>OpenCV:</strong> For image processing tasks, including edge detection, color thresholding, and line detection.</li>
    <li><strong>NumPy:</strong> For matrix and array operations.</li>
    <li><strong>Matplotlib:</strong> (Optional) For visualizing the intermediate steps during debugging.</li>
    <li><strong>SciPy:</strong> For clustering (if used for cone grouping).</li>
</ul>

<h2>How to Run</h2>

<ol>
    <li><strong>Clone the repository:</strong>
        <pre><code>git clone https://github.com/yourusername/wisconsin-perception-challenge.git
cd wisconsin-perception-challenge
        </code></pre>
    </li>
    <li><strong>Install the dependencies:</strong>
        <pre><code>pip install -r requirements.txt</code></pre>
    </li>
    <li><strong>Run the Code:</strong>
        <pre><code>python detect_boundaries.py input_image.png</code></pre>
    </li>
    <li><strong>Output:</strong>
        <p>The processed image will be saved as <code>answer.png</code>.</p>
    </li>
</ol>

<h2>Resources</h2>
<ul>
    <li><a href="https://docs.opencv.org/4.x/d9/df8/tutorial_root.html">OpenCV Documentation</a></li>
    <li><a href="https://docs.opencv.org/4.x/da/d22/tutorial_py_canny.html">Canny Edge Detection</a></li>
    <li><a href="https://docs.opencv.org/4.x/da/d6e/tutorial_py_houghlines.html">Hough Line Transformation</a></li>
</ul>

<h2>Notes</h2>
<p>The code is modular and documented to improve readability. Feel free to modify parameters such as the threshold values and blur kernels to adapt to different images. The solution can be further improved by incorporating machine learning techniques to classify and detect cones more accurately in complex environments.</p>

</body>
</html>
