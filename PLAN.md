# Plan: Handwritten Digit Recognition on MNIST

Everything lives in a single notebook: `mnist_experiments.ipynb`.

## 1. Problem
Classify 28×28 grayscale handwritten digits into 10 classes (0–9). The secondary dataset is MNIST, loaded with `keras.datasets.mnist.load_data()`.

## 2. Data
- 60,000 training images and 10,000 test images
- Exploratory look: class distribution, sample images, pixel statistics
- Preprocessing: scale pixels to [0, 1], reshape for MLP (flatten) and CNN (28×28×1) inputs, one-hot or sparse labels
- Splitting: hold out 10% of the training set for validation and keep the test set untouched for the final evaluation
- Optional: 5-fold cross-validation on the best model to show that results are stable

## 3. Models (experiments)
| ID | Model | Purpose |
|----|-------|---------|
| E1 | Simple MLP (Dense 128 → 10) | Baseline |
| E2 | Deeper MLP + Dropout | Effect of depth and regularization |
| E3 | Basic CNN (Conv → Pool → Dense) | Effect of convolution |
| E4 | Deeper CNN + BatchNorm + Dropout | Stronger architecture |
| E5 | Best CNN + data augmentation | Generalization |

## 4. Learning Strategy & Tuning
- Loss: sparse categorical cross-entropy; metric: accuracy
- Optimizers to compare: SGD, Adam, RMSprop
- Hyperparameters to vary: learning rate, batch size, number of epochs, dropout rate
- Callbacks: EarlyStopping and ReduceLROnPlateau
- Fixed random seed for reproducibility

## 5. Evaluation
- Accuracy and loss curves for each experiment
- Test accuracy, confusion matrix, and classification report (precision, recall, F1)
- Examples of misclassified digits
- Summary table comparing all experiments (accuracy, parameter count, training time)

## 6. Notebook Structure
1. Setup and imports
2. Load and explore the data
3. Preprocessing and splitting
4. Helper functions (train, plot, evaluate)
5. Experiments E1–E5
6. Hyperparameter / optimizer comparison
7. Results summary and best model
8. Conclusion

## 7. Map to the Presentation Slides
- Slide 3 (problem case): Section 1
- Slide 4 (data and splitting): Section 2
- Slide 5 (architecture): Section 3
- Slide 6 (learning strategy and tuning): Section 4
- Slides 7–9 (experiment results): Section 5
- Slide 10 (conclusion): notebook conclusion
