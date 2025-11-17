# 🍅 AI Tomato Sorting with YOLOv8

![GitHub License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python Version](https://img.shields.io/badge/python-3.9%2B-blue)

This repository contains the code and documentation for an AI-powered object detection model used for real-time tomato sorting. The model is built using **YOLOv8** and is trained to classify tomatoes into different categories (e.g., ripe, unripe, defective) to automate and improve agricultural processing.


> A short GIF or screenshot showing your model in action would be perfect here.

---

## 📖 Table of Contents

* [Project Overview](#-project-overview)
* [System Architecture](#%EF%B8%8F-system-architecture)
* [Techstack](#-techstack)
* [Getting Started](#-getting-started)
    * [Prerequisites](#prerequisites)
    * [Installation](#installation)
* [Usage](#-usage)
    * [1. Data Preparation](#1-data-preparation)
    * [2. Training](#2-training)
    * [3. Inference](#3-inference)
* [Results & Demo](#-results--demo)
* [Contributing](#-contributing)
* [License](#-license)

---

## 📋 Project Overview

The main goal of this project is to create an efficient and accurate automated sorting system for tomatoes. By leveraging computer vision and deep learning, this model can identify and classify tomatoes on a conveyor belt or in a batch, reducing manual labor and increasing sorting consistency.

The model is trained to detect the following classes:
* `ripe`
* `unripe`
* `defective` (e.g., bruised, moldy, or cracked)

This system can be integrated with mechanical sorters (e.g., robotic arms, air jets) to physically separate the tomatoes based on the model's predictions.

---

## ⚙️ System Architecture

This diagram shows the high-level workflow of the project, from data collection to final deployment on the sorting line.

![Project Flowchart](assets/flowchart.png)

> **Note:** To generate this image, you can use a tool like **Mermaid.js** (as we discussed).
>
> 1.  Create your flowchart in a tool like [Mermaid.live](https://mermaid.live).
> 2.  Export the diagram as a PNG file.
> 3.  Create a folder named `assets` in your GitHub repository.
> 4.  Place the `flowchart.png` file inside the `assets` folder. The image will then show up here automatically.

---

## 🛠️ Techstack

This project utilizes the following key technologies and libraries:

* **Python 3.9+**: The core programming language.
* **Ultralytics YOLOv8**: The pre-trained model and framework used for object detection.
* **PyTorch**: The deep learning library that YOLOv8 is built on.
* **OpenCV (cv2)**: Used for image processing, loading video streams, and drawing bounding boxes.
* **Roboflow** (Recommended): A platform for dataset management, annotation, and augmentation.
* **NumPy**: For efficient numerical operations.

---

## 🚀 Getting Started

Follow these instructions to get a copy of the project up and running on your local machine.

### Prerequisites

* Python 3.9 or higher
* Git

### Installation

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/](https://github.com/)[YOUR_USERNAME]/[YOUR_REPO_NAME].git
    cd [YOUR_REPO_NAME]
    ```

2.  **Create a virtual environment (Recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3.  **Install the required packages:**
    ```bash
    pip install -r requirements.txt
    ```
    > **Note:** You can create a `requirements.txt` file by running `pip freeze > requirements.txt` after installing the packages below:
    > ```bash
    > pip install ultralytics opencv-python numpy
    > ```

---

## 🏃 Usage

You can use this repository to train the model from scratch or to run inference using the pre-trained weights.

### 1. Data Preparation

Your dataset must be in YOLO format. It should have a `data.yaml` file that looks like this:

```yaml
# data.yaml
train: ../dataset/train/images
val: ../dataset/val/images

# Class names
names:
  0: ripe
  1: unripe
  2: defective
```

### 2. Training

To train the model on your custom dataset, run the following command. The results will be saved to a `runs/` folder.

```bash
# Start training from a pre-trained YOLOv8 'small' model
yolo task=detect mode=train model=yolov8s.pt data=data.yaml epochs=100 imgsz=640
```

### 3. Inference

To run detection on a new image, video, or webcam stream, use the `predict` mode. Make sure to point to your best-trained model (e.g., `runs/detect/train/weights/best.pt`).

* **On an Image:**
    ```bash
    yolo task=detect mode=predict model=runs/detect/train/weights/best.pt source=path/to/your/image.jpg
    ```

* **On a Video:**
    ```bash
    yolo task=detect mode=predict model=runs/detect/train/weights/best.pt source=path/to/your/video.mp4
    ```

* **On a Webcam (Live):**
    ```bash
    yolo task=detect mode=predict model=runs/detect/train/weights/best.pt source=0
    ```

---

## ✨ Results & Demo

Here is the model performing inference on a test image. The model correctly identifies ripe and unripe tomatoes with high confidence.

![Example of detection results](assets/demo_image.jpg)

> **Tip:** Include one or two of your best detection results here. Screenshots of the `results.png` from your `runs/` folder are perfect for this.

---

## 🤝 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.

If you have a suggestion that would make this better, please fork the repo and create a pull request.
1.  Fork the Project
2.  Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3.  Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4.  Push to the Branch (`git push origin feature/AmazingFeature`)
5.  Open a Pull Request

---

## 📜 License

Distributed under the MIT License. See `LICENSE` file for more information.
