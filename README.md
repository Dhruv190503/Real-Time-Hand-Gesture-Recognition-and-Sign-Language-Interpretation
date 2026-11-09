# Real-Time Hand Gesture Recognition

A computer vision and deep learning project that recognizes static hand gestures representing the English alphabet (A–Z) and the digit **0**. The system uses OpenCV for image preprocessing and a Convolutional Neural Network (CNN) built with TensorFlow/Keras for gesture classification. It also includes a real-time webcam interface for predicting hand gestures.

## Overview

This project explores gesture-based human-computer interaction using image processing and deep learning.

A CNN is trained on labeled hand gesture images to classify each image into one of 27 categories: the letters A–Z and the digit 0. The trained model is then used in a webcam-based application to perform real-time gesture predictions.

## Features

- **27-class classification:** Recognizes static hand gestures corresponding to A–Z and 0.
- **Image preprocessing:** Uses grayscale conversion, Gaussian blurring, adaptive thresholding, and Otsu thresholding.
- **CNN-based classification:** Learns visual features through convolutional and max-pooling layers.
- **Model regularization:** Uses dropout layers to help reduce overfitting.
- **Model checkpointing:** Saves model checkpoints based on validation loss.
- **Real-time prediction:** Uses a webcam to capture and classify hand gestures.
- **Text generation:** Converts predicted gesture labels into a text sequence.

## Tech Stack

| Category | Technologies |
|---|---|
| Programming Language | Python |
| Deep Learning | TensorFlow, Keras |
| Computer Vision | OpenCV |
| Data Processing | NumPy |
| Visualization | Matplotlib |
| Development Environment | Jupyter Notebook |

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

The model is compiled using the **Adam optimizer** and categorical cross-entropy loss, with accuracy as the evaluation metric.

## Image Preprocessing

The same preprocessing pipeline is used during training and real-time inference:

1. Convert the input image to grayscale.
2. Apply Gaussian blur to reduce noise.
3. Apply adaptive Gaussian thresholding.
4. Apply Otsu thresholding with a minimum threshold value of 70.
5. Resize the processed image to 128 × 128 pixels.
6. Normalize pixel values to the range [0, 1].
7. Reshape the image into the format expected by the CNN: `(1, 128, 128, 1)` for a single prediction.

## Dataset Structure

The training dataset is organized into folders corresponding to each gesture class:

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

Each folder contains images belonging to its corresponding class.

**Note:** The original dataset is not included in this repository. You will need to provide your own dataset or configure the notebook to use your existing dataset.

## Installation

Clone the repository:

```bash
git clone https://github.com/<your-username>/<your-repository>.git
cd <your-repository>
```

Install the required dependencies:

```bash
pip install numpy opencv-python tensorflow matplotlib jupyter
```

## Training the Model

1. Place the dataset in the expected folder structure.
2. Open the training Jupyter notebook.
3. Update the dataset path to match your local environment.
4. Run the notebook cells to load and preprocess the images.
5. Train the CNN using the configured training and validation split.
6. Review the training and validation loss and accuracy plots.
7. Save the trained model.

The training configuration includes:

- Maximum epochs: **50**
- Validation split: **30%** of the training data
- Optimizer: **Adam**
- Loss function: **Categorical Cross-Entropy**
- Checkpoint monitoring: **Validation Loss**

The trained model is saved as:

```text
asl_classifier50.keras
```

## Real-Time Gesture Recognition

The second notebook uses the trained model to recognize hand gestures through a webcam.

To run the real-time application:

1. Train the model or obtain the trained `asl_classifier50.keras` file.
2. Place the model file in the directory from which the inference notebook is run.
3. Connect a webcam to your computer.
4. Open the real-time inference notebook.
5. Run the cells to initialize the webcam and load the model.
6. Position your hand inside the displayed region of interest.
7. The model predicts the gesture and displays the corresponding label.

Press **ESC** to exit the webcam application.

**Note:** The current inference implementation uses a fixed region of interest. Prediction accuracy can depend on hand positioning, lighting, background, and camera conditions.

## Model Evaluation

The training notebook evaluates the model using a held-out test split and plots training and validation accuracy and loss.

The notebook reports a test accuracy of approximately **99.84%**. This result reflects performance on the dataset split used during training and should not be interpreted as a guarantee of real-world webcam accuracy.

Independent testing across different users, backgrounds, lighting conditions, and camera positions is recommended to assess generalization.

## Applications

- Gesture-based human-computer interaction
- Hand gesture recognition
- Assistive technology prototypes
- Gesture-controlled applications
- Foundations for sign-language-related recognition systems

**Scope:** This project classifies 27 static hand gesture classes. It is not a complete sign-language translation system. Full sign-language understanding can require temporal information, facial expressions, additional gestures, and linguistic context.

## Future Improvements

- Implement prediction smoothing to reduce unstable frame-by-frame predictions.
- Improve character-entry logic to prevent repeated predictions while holding a gesture.
- Add a neutral or blank gesture class.
- Improve robustness to different lighting conditions, backgrounds, and hand positions.
- Evaluate the model on an independent dataset with images from different users.
- Expand the gesture vocabulary.
- Integrate gesture recognition with external applications.

---

**Developed using Python, OpenCV, TensorFlow, and Keras.**
