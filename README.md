# Real-Time Hand Gesture Recognition

A computer vision and deep learning project that recognizes hand gestures representing the English alphabet (A–Z) and the digit **0**. The system processes hand images using OpenCV and classifies them with a Convolutional Neural Network (CNN), with potential applications in gesture-based human-computer interaction and assistive technology.

## Overview

Traditional input devices are not always the most intuitive way to interact with computers. This project explores gesture-based interaction by combining image processing and deep learning to identify hand gestures.

The model is trained on labeled hand gesture images and uses a CNN to classify each image into one of 27 categories.

## Features

- **27-class classification:** Recognizes gestures corresponding to A–Z and 0.
- **Image preprocessing:** Applies grayscale conversion, Gaussian blurring, adaptive thresholding, and image resizing.
- **CNN-based classification:** Uses convolutional and max-pooling layers to learn visual features.
- **Model regularization:** Uses dropout layers to help reduce overfitting.
- **Model checkpointing:** Saves model checkpoints based on validation loss.
- **Extensible design:** Provides a foundation for real-time gesture interfaces and assistive applications.

## Tech Stack

- **Language:** Python
- **Deep Learning:** TensorFlow / Keras
- **Computer Vision:** OpenCV
- **Data Processing:** NumPy
- **Visualization:** Matplotlib

## Model Architecture

The project uses a Convolutional Neural Network with the following architecture:

| Layer | Configuration |
|---|---|
| Input | 128 × 128 grayscale image |
| Convolution | 32 filters, 3 × 3 kernel, ReLU |
| Max Pooling | 2 × 2 |
| Convolution | 32 filters, 3 × 3 kernel, ReLU |
| Max Pooling | 2 × 2 |
| Flatten | Converts feature maps into a vector |
| Fully Connected | 128 units, ReLU |
| Dropout | 0.40 |
| Fully Connected | 96 units, ReLU |
| Dropout | 0.40 |
| Fully Connected | 64 units, ReLU |
| Output | 27 units, Softmax |

The network is trained using the **Adam optimizer** and categorical cross-entropy loss, with accuracy tracked as a training metric.

## Image Preprocessing

Each input image goes through the following preprocessing pipeline:

1. Load the image using OpenCV.
2. Convert the image to grayscale.
3. Apply Gaussian blur to reduce noise.
4. Apply adaptive thresholding and Otsu thresholding to emphasize the hand shape.
5. Resize the processed image to 128 × 128 pixels.
6. Normalize pixel values to the range [0, 1].
7. Reshape the image for input into the CNN.

## Dataset Structure

Organize the training images into folders named after their respective gesture labels:

```text
dataset/
└── train/
    ├── 0/
    ├── A/
    ├── B/
    ├── C/
    ├── ...
    ├── X/
    ├── Y/
    └── Z/
```

Each folder should contain images belonging to its corresponding class.

> **Note:** The dataset used in the original notebook is stored locally. You must provide your own dataset or configure the path to your existing dataset before running the notebook.

## Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

Install the required Python packages:

```bash
pip install numpy opencv-python tensorflow matplotlib jupyter
```

If your environment uses a standalone Keras installation, ensure it is compatible with your TensorFlow version.

## Training

1. Place the dataset in the expected folder structure.
2. Open the Jupyter notebook.
3. Update the dataset path in the notebook to match your local environment.
4. Run the notebook cells to load, preprocess, and encode the images.
5. Train the CNN using the configured training and validation split.
6. Review the training and validation loss and accuracy plots.
7. Save the trained model.

The notebook trains for up to **50 epochs**, uses a **30% validation split**, and saves the best checkpoint according to validation loss.

The final model is saved as:

```text
asl_classifier50.keras
```

Training duration and performance depend on the dataset, hardware, and software environment.

## Model Evaluation

The notebook plots training and validation loss and accuracy to help assess model learning and generalization.

No verified test-set accuracy is reported here. Evaluate the trained model on unseen images before reporting final performance metrics.

## Applications

- Gesture-based human-computer interaction
- Assistive technology prototypes
- Hand gesture classification
- Foundations for sign-language-related recognition systems
- Gesture-controlled applications and devices

**Scope:** This project classifies 27 static gesture classes. It does not, by itself, establish full sign-language understanding, which can require additional gestures, temporal information, facial expressions, and contextual interpretation.

## Future Improvements

- Add a real-time webcam inference interface.
- Evaluate performance on an independent test dataset.
- Improve robustness to lighting, background, and hand-position variations.
- Add confidence thresholds and prediction smoothing.
- Expand the supported gesture vocabulary.
- Integrate gesture predictions with external applications or devices.

## License

Add a license file to specify how others may use, modify, and distribute this project.

---

**Developed as a computer vision and deep learning project using Python, OpenCV, and TensorFlow/Keras.**
