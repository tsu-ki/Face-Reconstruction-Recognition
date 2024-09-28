# Face-Reconstruction-Recognition System: AI-Powered CCTV Security System

[![GitHub license](https://img.shields.io/github/license/tsu-ki/Face-Reconstruction-Recognition)](https://github.com/your-username/Face-Reconstruction-Recognition/blob/main/LICENSE)

## Overview

This project addresses the challenge of enhancing security and surveillance by accurately reconstructing and recognizing faces from low-quality CCTV footage. We leverage the power of CodeFormer, a state-of-the-art face restoration model, and Facenet for facial feature extraction, coupled with MongoDB Atlas Vector Search for efficient identification. 

## Key Features

*   **Face Restoration with CodeFormer**: Employs CodeFormer's innovative VQGAN-Transformer architecture to enhance faces from degraded CCTV footage, overcoming challenges like low resolution, noise, and blur.
*   **Facial Recognition with Facenet**: Extracts discriminative facial features using Facenet, enabling accurate identification by comparing against a database of known individuals.
*   **Efficient Database Search**: Utilizes MongoDB Atlas Vector Search and its approximate k-nearest neighbors algorithm for fast and scalable face matching.
*   **Streamlined Video Processing**: Implements a robust pipeline for frame extraction, face detection, alignment, restoration, and recognition.
*   **User-Friendly Interface**: (To be developed) A web interface will allow administrators to manage alerts, review unfamiliar individuals, and update the database.

## Methodology

1.  **Input Footage**: Processes video footage from a specified directory.
2.  **Frame Extraction**: Extracts frames at a defined rate (e.g., one frame every 3 seconds) using OpenCV.
3.  **Face Detection & Alignment**: Employs the RetinaFace Resnet50 model to detect and align faces within each frame.
4.  **Face Restoration**: Enhances the quality of detected faces using CodeFormer.
5.  **Feature Extraction**: Extracts facial feature vectors using Facenet.
6.  **Matching & Recognition**: Compares extracted feature vectors against a database of known individuals using MongoDB Atlas Vector Search.
7.  **Alerting & Management**: (Future implementation) A web interface will provide alerts and management tools for administrators.

## Getting Started

### Prerequisites

*   **Python 3.x**: Ensure you have Python 3.x installed.
*   **Dependencies**: Install the required libraries using:
    ```bash
    pip install -r requirements.txt
    ```
*   **Pretrained Models**: Download the necessary pretrained models using the provided scripts:
    ```bash
    python download_pretrained_models.py
    ```
*   **MongoDB Atlas Setup**: 
    * Set up a MongoDB Atlas cluster and enable Vector Search.
    * Configure your connection credentials in `settings.py`.

### Running the Model

1.  **Frame Extraction (for videos)**:
    *   Place your video files in the `videos/ch5` directory (or modify the `VIDEO_DIRPATH` in `settings.py`).
    *   Run the frame extractor:
        ```bash
        python main.py
        ```
    *   This will extract frames from your videos and save them in the `out_dir` directory.

2.  **Face Restoration & Recognition**:
    *   For **images**:
        ```bash
        python inference_codeformer.py -i <path_to_your_image>
        ```
    *   For **videos**:
        ```bash
        python inference_codeformer.py -i <path_to_your_video>
        ```
    *   The restored faces will be saved in the `results` directory, and their embeddings will be sent to the MongoDB Atlas database for recognition.

3.  **Other Tasks**:
    *   **Inpainting**:
        ```bash
        python inference_inpainting.py -i <path_to_your_masked_image> --mask_path <path_to_your_mask>
        ```
    *   **Colorization**:
        ```bash
        python inference_colorization.py -i <path_to_your_grayscale_image>

## Contributing

We welcome contributions! Please see our [CONTRIBUTING.md](CONTRIBUTING.md) for guidelines.

## License

This project is licensed under the [MIT License](LICENSE).

## Acknowledgments

*   We extend our gratitude to the creators of CodeFormer and Facenet for their groundbreaking work.
*   We also acknowledge the contributions of the open-source community for providing valuable tools and resources.
