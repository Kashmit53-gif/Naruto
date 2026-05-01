## AI-Driven Gesture Controlled Cloning (SHINOBI AR)


 An Interactive Augmented Reality Experiment in Human-Computer Interaction (HCI)


# Scholarship Statement of Intent

This project was developed to explore the intersection of Computer Vision (CV), Real-Time Web Graphics, and Augmented Reality (AR). My goal was to move beyond traditional button-based interfaces and create an immersive, hands-free experience where the user’s physical gestures serve as the primary input for complex digital manipulations—specifically, real-time background subtraction and entity replication.


# Technical Core

The application utilizes a multi-model pipeline to process live video feed at 60FPS, achieving low-latency interaction through browser-based hardware acceleration.


# The AI Pipeline

•	MediaPipe Hands: Used to detect and track 21 3D hand landmarks. I implemented a custom Gesture Engine to calculate the Euclidean distance and relative Y-coordinates of finger tips to recognize specific gestures (Thumbs Up, Fist).
•	MediaPipe Selfie Segmentation: A machine learning model that produces a real-time alpha mask of the user. This allows for "pixel-perfect" extraction of the user’s silhouette without the need for a physical green screen.
•	Offscreen Rendering: To optimize performance, I utilized offscreen HTML5 canvases to cache segmented frames, allowing for the simultaneous rendering of multiple high-resolution "clones" without dropping frames.


# Features & Innovation

1. Dynamic Entity Replication
When the "Chakra" meter reaches 100% via the Thumbs Up gesture, the system captures the current segmented frame and initializes a Clone Array. These clones are layered within a 3D-simulated environment using:
•	Depth Sorting: Clones are arranged in an elliptical ring with varying scales to simulate perspective.
•	Transparency Gradients: Farther clones have lower opacity to emphasize depth of field.

2. Procedural Audio & Visual SFX
•	Web Audio API: Rather than just playing MP3s, the system uses an AudioContext to synthesize procedural "energy" sounds (sawtooth and sine wave sweeps) that react to user input.
•	Particle Systems: A custom-built class-based particle engine handles smoke "poofs" and energy orbs using physics-based velocity and life-cycle management.

3. Shinobi HUD (Heads-Up Display)
The interface features a futuristic "System" aesthetic designed for clarity during live demonstrations:
•	Real-time Latency Monitoring (ms tracking).
•	Dynamic Chakra Meter linked to gesture confidence levels.
•	System Event Log for real-time status updates.


# Live Demo Instructions

To ensure the best performance during the scholarship presentation:
	1.	Lighting: Ensure the face and hands are well-lit to assist the MediaPipe models in landmark detection.
	2.	The "Kage Bunshin" (Spawn) Gesture: Hold a Thumbs Up with one or both hands. The HUD will show the chakra charging. Once full, clones will appear in a radial formation.
	3.	The "Dispel" Gesture: Close your hand into a Fist. This triggers a global "poof" particle effect and clears the clone array, resetting the system state.


# Tech Stack

Category	Technology Used
Language	JavaScript (ES6+), HTML5, CSS3
AI Models	MediaPipe (Hand Tracking & Selfie Segmentation)
Graphics	HTML5 Canvas API (2D Context)
Audio	Web Audio API & Speech Synthesis
Styling	CSS Grid/Flexbox, Glassmorphism, Bungee Fonts


# Challenges Overcome

•	Synchronization: Aligning the hand-tracking data with the segmentation mask required precise frame-timing to ensure that particles appeared exactly at the fingertip locations.
•	Resource Management: Running two heavy ML models in a single browser thread is demanding. I optimized the loop by using requestAnimationFrame and limiting segmentation processing to the required resolution rather than the full display size.


# Future Roadmap

•	Multi-Gesture Library: Expanding the system to recognize more complex hand signs for different elemental effects.
•	WebGPU Integration: Migrating the canvas rendering to WebGPU for even more complex particle physics.
•	Multi-Player Sync: Utilizing WebRTC to allow two users to see each other's clones in a shared AR space.

# Demo Video
