# Webcam 3D Graphics Tracker

This project uses your webcam to track colored objects (like your phone screen) and uses that movement to scale and rotate 3D shapes rendered in real-time. It is split into two parts working together: a Python tracking script and a custom C++ graphics engine. 

## How It Works (The Tech Stuff)
*   **The Python Side (Image Processing)**: Uses OpenCV to open the webcam, applies a blur filter, and uses the HSV color space to find specific colors on the screen. It calculates the X and Y coordinates of the color and sends that data over a local UDP socket to the C++ program.
*   **The C++ Side (3D Graphics)**: Uses SDL3 and Winsock2 to receive the UDP data. It uses 3D homogeneous coordinates and matrix multiplication to scale, rotate, and project 3D shapes onto a 2D screen. Instead of using built-in drawing tools, it draws the shapes manually using the Bresenham midpoint line drawing algorithm.

## Controls & Features
To use the program, open a fully red, blue, or green image on your phone screen and hold it up to the camera. The 3D shapes will react on your computer screen:
*   **Red Screen**: Draws an interactive 3D cube.
*   **Blue Screen**: Draws an interactive 3D pyramid.
*   **Green Screen**: Draws a cube that spins on its own.
*   **Movement**: Moving the phone closer to the camera scales the 3D shape up, and moving it left or right rotates the shape.

## How to Run It
1.  **Prerequisites**: Make sure you have Python installed. You will also need Visual Studio installed for the C++ part, with the SDL3 library downloaded.
2.  **Python Setup**: Open a terminal and install the required libraries by running `pip install opencv-python numpy`.
3.  **Start the Tracker**: Open `tracker.py` in Visual Studio Code and click run, or type `python tracker.py` in your terminal.
4.  **Start the Graphics**: Open the C++ project file in Visual Studio and start the program.

## How to Close
*   **Python**: Click on the video window to select it, then press the `q` key on your keyboard.
*   **C++**: Go back to Visual Studio and click the red "Stop Debugging" button at the top.
