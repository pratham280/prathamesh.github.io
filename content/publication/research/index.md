---
title: 'Design and Development of a Low-Cost Quadruped Robot'

# Authors
# If you created a profile for a user (e.g. the default `admin` user), write the username (folder name) here
# and it will be replaced with their full name and linked to their profile.
authors:
  - admin
  - Sumeet Adsul
  - Samyak Ghangale

# Author notes (optional)
author_notes:
  - 'co-athor'
  - 'Equal contribution'

date: '2025-05-11T00:00:00Z'
doi: ''

# Schedule page publish date (NOT publication's date).
publishDate: '2025-05-10T00:00:00Z'

# Publication type.
# Accepts a single type but formatted as a YAML list (for Hugo requirements).
# Enter a publication type from the CSL standard.
publication_types: ['paper-conference']

# Publication name and optional abbreviated publication name.
publication: In *International Conference on CyberTech and Smart System*
publication_short: In *ICCSS*

abstract: This paper presents the design and development of a low-cost quadruped robot inspired by Boston Dynamics’ Spot, aimed at academic and research accessibility. Utilizing ESP32 and Raspberry Pi as the control units, the robot integrates MG996 servo motors, an MPU6050 IMU, ultrasonic sensors, and an ESP32-CAM for terrain navigation and surveillance. The system features 3D-printed modular components and a custom web interface for control and video streaming. Stable locomotion was achieved using crawl and trot gaits with real-time posture correction enabled by sensor fusion and PID control. The robot serves as a cost-effective, extensible platform for exploring legged locomotion, embedded systems, and autonomous mobility.

# Summary. An optional shortened abstract.
summary: This paper details a low-cost quadruped robot built using ESP32 and Raspberry Pi for terrain navigation and surveillance. Featuring 3D-printed parts, servo-driven legs, sensor-based posture control, and live video streaming, the robot offers stable movement and remote operation. It serves as an accessible platform for robotics education and research.

tags:
  - Quadruped Robot
  - ESP32
  - Raspberry Pi

# Display this page in the Featured widget?
featured: true

# Custom links (uncomment lines below)
# links:
# - name: Custom Link
#   url: http://example.org

url_pdf: '/publication/research/research.pdf'
url_code: 'https://github.com/pratham280/Quadruped_Sheru'
url_dataset: ''
url_poster: ''
url_project: ''
url_slides: ''
url_source: 'https://novaspotmicro.com/'
url_video: ''

# Featured image
# To use, add an image named `featured.jpg/png` to your page's folder.
image:
  caption: 'Image credit: [**Unsplash**](https://unsplash.com/photos/a-close-up-of-a-robot-that-is-yellow-NnYbRvZUi9A?utm_content=creditShareLink&utm_medium=referral&utm_source=unsplash)'
  focal_point: ''
  preview_only: false

# Associated Projects (optional).
#   Associate this publication with one or more of your projects.
#   Simply enter your project's folder or file name without extension.
#   E.g. `internal-project` references `content/project/internal-project/index.md`.
#   Otherwise, set `projects: []`.
projects:
  - Quaderuped robot aka "Sheru"

# Slides (optional).
#   Associate this publication with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides: "example"` references `content/slides/example/index.md`.
#   Otherwise, set `slides: ""`.
# slides: example
---
<!-- 
{{% callout note %}}
Click the _Cite_ button above to demo the feature to enable visitors to import publication metadata into their reference management software.
{{% /callout %}}

{{% callout note %}}
Create your slides in Markdown - click the _Slides_ button to check out the example.
{{% /callout %}}

Add the publication's **full text** or **supplementary notes** here. You can use rich formatting such as including [code, math, and images](https://docs.hugoblox.com/content/writing-markdown-latex/). -->

## Low-Cost Quadruped Robot

This project showcases the development of a low-cost quadruped robot built using ESP32 and Raspberry Pi. Inspired by Boston Dynamics' Spot, the goal was to create an accessible platform for students and researchers to explore legged locomotion, posture control, and basic remote surveillance. By combining off-the-shelf electronics with 3D-printed mechanical components, the robot achieves stable walking and real-time video streaming at a significantly lower cost.

The hardware architecture includes ESP32 as the low-level controller responsible for servo actuation and sensor data processing, while the Raspberry Pi manages higher-level tasks such as hosting the web interface and handling video streams. Each leg is driven by three MG996R servo motors, providing two degrees of freedom—hip and knee—for executing crawl and trot gait patterns. Orientation feedback is enabled through the MPU6050 IMU, helping the robot maintain a level posture during movement. For vision and monitoring, an ESP32-CAM module streams live video to a browser-based dashboard built with Flask.

The robot is powered by a 3S 4000mAh Li-ion battery, regulated using a buck converter to supply stable voltages to servos and logic components. The modular 3D-printed frame, designed in Fusion 360, simplifies both assembly and maintenance, making it ideal for iterative prototyping. Components such as servo brackets, sensor mounts, and the main control hub were designed to fit snugly into the printed body.

A key feature of this platform is its responsive web interface, accessible over Wi-Fi from any PC or smartphone. The interface provides manual control via keyboard or joystick, as well as a live video feed for remote navigation. Communication between the ESP32 and Raspberry Pi is achieved through UART serial, with optional fallback to Wi-Fi.

This robot serves as an excellent entry point into quadruped robotics, real-time embedded programming, and robotic perception systems. Future improvements could include integration with computer vision libraries for object tracking, use of LIDAR for SLAM-based mapping, or implementation of adaptive gaits through machine learning. The entire system was built on a modest budget of approximately ₹12,000–14,000, making it highly suitable for academic projects, robotics clubs, and early-stage research.

---

### 📌 Overview

This project demonstrates the design and development of a modular four-legged robot that can:
- Walk using crawl and trot gaits
- Maintain posture using IMU-based feedback
- Stream live video via ESP32-CAM
- Be remotely controlled using a web-based dashboard

---

### ⚙️ Hardware Used
- **ESP32** – Real-time servo control
- **Raspberry Pi 4** – Web UI, vision streaming
- **MG996R Servo Motors (x12)** – 3 DOF per leg
- **MPU6050 IMU** – Posture sensing
- **HC-SR04 Sensors** – Obstacle detection
- **ESP32-CAM** – Real-time video feed
- **3S 4000mAh Li-ion Battery** – Power supply
- **3D Printed Frame** – Designed in Fusion 360

---

### 🧠 Software Architecture
- **ESP32 (Arduino IDE)** handles:
  - Gait logic
  - Servo control
  - IMU feedback
- **Raspberry Pi (Flask App)** handles:
  - Web interface (keyboard/joystick)
  - Video stream display
  - Serial/WiFi communication with ESP32

---

### 🎮 Control Interface
- Access through mobile/PC via Flask dashboard
- Manual commands:
  - Forward / Backward
  - Rotate Left / Right
  - Live video feed
- Future upgrades:
  - Vision-based object tracking
  - Terrain-aware gait adaptation
  - ROS2 integration

---

### 📷 Images
> Insert photos or videos of CAD model, hardware, walking gait, etc.

---

### 🚀 Key Features
- Stable walking on flat terrain
- Real-time posture correction
- Wi-Fi controlled user interface
- Modular and printable design
- Budget-friendly (~₹12,000–14,000)

---

### 🧪 Applications
- Academic research
- Robotics education
- Surveillance demos
- Terrain navigation tests

---

### 👨‍💻 Contributors
- Samyak R. Ghangale  
- Sumeet Adsul  
- Prathamesh J. Mawale   

<!-- --- -->
<!-- 
### 📄 License
This project is licensed under the **Apache License 2.0**. -->

---

## 📝 Notes
- Based on SpotMicroESP32 open-source work
- Designed and tested in indoor environments
- Expandable for autonomous navigation, SLAM, and vision tasks

---

