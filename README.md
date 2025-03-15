VIRTUAL MOUSE USING HAND GESTURE

The project titled “VIRTUAL MOUSE USING HAND GESTURE" utilizes MediaPipe, OpenCV, and PyAutoGUI to implement hand gesture-based control of a computer cursor. It uses a webcam to track hand landmarks in real-time, enabling users to move the cursor, perform left and right clicks, and simulate drag-and-drop actions using natural gestures. MediaPipe provides robust hand tracking, OpenCV facilitates real-time video processing, and PyAutoGUI enables interaction with the operating system's cursor functions. 
This project lies in the field of Computer Vision . It bridges the gap between traditional input devices like a mouse and gesture-based controls, opening up  for  touchless control mechanisms 
.Hand Gesture Detection:-

The code uses Mediapipe's hand detection to track the hand and its landmarks (such as fingers and their tips).

Only one hand is being tracked (max_num_hands=1), with a detection confidence of 70% (min_detection_confidence=0.7).

The position of the index finger tip and thumb tip is detected and used to calculate the pinch distance for determining gestures like clicks.

2. Mouse Movement

The position of the index finger tip is scaled to the screen size using PyAutoGUI (pyautogui.moveTo()).

This means wherever you move your index finger on the webcam, the mouse cursor moves to the corresponding position on the screen.

Frame flipping (cv2.flip(frame, 1)) is used to create natural hand movements. Without this, moving your hand to the right would move the cursor left, and vice versa, which could feel unnatural.


3. Left-Click Detection

When the thumb and index finger tip come close together, a pinch gesture is detected (pinch_distance < 0.05), which
 triggers a left-click (pyautogui.click()).
The system also starts a drag (pyautogui.mouseDown()) if the pinch gesture continues, allowing for dragging actions.
Once the pinch gesture is released, the drag stops (pyautogui.mouseUp()).

Result:
You can left-click by pinching your thumb and index finger together.
If you hold the pinch gesture, you can drag items on the screen. Releasing the pinch will stop the drag.



4.Right-Click Detection

The code also detects a right-click gesture by checking the distance between the index finger and middle finger.
If these two fingers come close (right_click_distance < 0.05), a right-click is triggered (pyautogui.click(button='right’)).
You can trigger a right-click by bringing the index and middle fingers close together. This is useful for opening context
 menus or performing other right-click actions.






5. Real-Time Performance
The program runs in real-time using the webcam feed. It continuously processes each frame to detect hand gestures and
  control mouse actions accordingly.
The program is responsive, though performance may vary depending on the hardware and lighting conditions.
 If your machine has a slow CPU or the lighting conditions are poor, the system might experience some latency or struggle to detect gestures.
![image](https://github.com/user-attachments/assets/5f74c567-5b59-4592-8919-43b4fdf01122)

