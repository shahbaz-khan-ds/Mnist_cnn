# MNIST Handwritten Digit Classification using CNN

## Project Overview
This project uses a Convolutional Neural Network (CNN) built with TensorFlow and Keras to classify handwritten digits from the MNIST dataset. Each image is a 28 × 28 grayscale image, and the model predicts one of ten classes (0–9).

## Dataset
- Dataset: MNIST (loaded using `tensorflow.keras.datasets.mnist`)
- Training images: 60,000
- Test images: 10,000
- Image dimensions: 28 × 28 pixels
- Image type: Grayscale
- Number of classes: 10 (digits 0–9)

The dataset is provided by Keras, so a separate manual download is not required when running the notebook in a supported TensorFlow environment.

## Workflow
1. Import the required Python libraries.
2. Load the MNIST dataset.
3. Inspect image shapes, labels, and sample images.
4. Normalize pixel values to the range 0–1.
5. Split the original training set into training and validation subsets (90% / 10%).
6. Build a CNN with convolutional, max-pooling, flatten, and dense layers.
7. Train the model using Adam and sparse categorical cross-entropy.
8. Apply early stopping based on validation loss.
9. Plot training and validation accuracy/loss.
10. Evaluate on the official test set.
11. Review precision, recall, F1-score, confusion matrix, and incorrect predictions.
12. Optionally classify a custom digit image.

## Model Architecture
- Input: 28 × 28 × 1
- Conv2D: 32 filters, 3 × 3, ReLU
- MaxPooling2D: 2 × 2
- Conv2D: 64 filters, 3 × 3, ReLU
- MaxPooling2D: 2 × 2
- Flatten
- Dense: 128 units, ReLU
- Output: 10 units, Softmax

## Preprocessing and Evaluation Notes
Image pixels are converted to `float32` and divided by 255 before splitting the original training set. This ensures that training, validation, and test images use the same scale. The official test set is kept separate from training and validation and is used only for final evaluation.

**Important correction:** The initial notebook version split the training images before normalizing only `x_train` and `x_test`. As a result, the split training/validation arrays remained on the 0–255 scale while the test array was on the 0–1 scale. The annotated notebook corrects this preprocessing order. The earlier reported 98.99% test accuracy should therefore not be treated as the verified result of the corrected workflow.

## Results
Final test accuracy and test loss: **To be recorded after running the corrected notebook.**

Do not report the earlier 98.99% value as the final result. Run the corrected notebook from top to bottom and replace this line with the measured test accuracy and loss.

## Technologies Used
- Python
- TensorFlow
- Keras
- NumPy
- Matplotlib
- scikit-learn
- Pillow

## How to Run
1. Open `MNIST_CNN_Annotated.ipynb` in Google Colab or Jupyter Notebook.
2. Run the cells from top to bottom.
3. The MNIST dataset will be loaded through Keras.
4. After training, check the test metrics in Section 9.
5. Optionally update the custom image path in Section 12 to test your own digit image.

## Repository Structure
```text
MNIST-CNN-Classification/
├── MNIST_CNN_Annotated.ipynb
└── README.md

```

## Limitations
- MNIST contains centered, low-resolution handwritten digits and is simpler than many real-world image datasets.
- Custom images may require additional preprocessing (centering, cropping, and background normalization) to match MNIST's image style.
- Prediction confidence is not the same as prediction correctness.
- Final performance must be reported from the corrected notebook's untouched test-set evaluation.

## Future Improvements
- Experiment with dropout and batch normalization.
- Compare alternative CNN architectures.
- Add image-centering and bounding-box preprocessing for custom inputs.
- Save and compare multiple model versions.
