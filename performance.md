# Visualize Learning Rate Schedule in ANN Models with ReduceLROnPlateau

This repository contains a Python script (`visualize_lr_plateau.py`) that demonstrates and visualizes the effect of the `ReduceLROnPlateau` callback in Keras on the learning rate during the training of a simple Artificial Neural Network (ANN) model.

The script uses TensorFlow/Keras to build and train a basic ANN for a binary classification task with synthetic data. It then utilizes Matplotlib to plot both the learning rate schedule and the validation loss over the training epochs, highlighting when the learning rate is reduced due to a plateau in the validation loss.

## Files

* `visualize_lr_plateau.py`: The main Python script containing the code for building, training, and visualizing the ANN with the `ReduceLROnPlateau` callback.

## Understanding the Visualization

The generated plots help visualize how the `ReduceLROnPlateau` callback works:

* **Learning Rate Schedule Plot:**
    * The y-axis (Learning Rate) is on a logarithmic scale to better visualize the reductions.
    * Red circles mark the epochs at which the learning rate was reduced because the validation loss had plateaued (stopped improving) for a certain number of epochs (`patience` parameter of the callback).
    * You will observe the learning rate starting at an initial value and then potentially dropping one or more times during training.

* **Validation Loss Plot:**
    * This plot shows the performance of the model on the validation dataset over the training epochs.
    * Ideally, you might observe that after a learning rate reduction, the validation loss might start to decrease again or stabilize, indicating that the lower learning rate is helping the model fine-tune its weights and potentially escape plateaus.

## Code Explanation

The `visualize_lr_plateau.py` script performs the following steps:

1.  **Imports necessary libraries:** `numpy`, `matplotlib.pyplot`, `tensorflow`, and `ReduceLROnPlateau`.
2.  **Defines a simple ANN model:** A sequential model with one hidden layer and an output layer for binary classification.
3.  **Generates synthetic data:** Creates random input features and binary labels.
4.  **Splits data:** Divides the data into training and validation sets.
5.  **Initializes the model and optimizer:** Sets up the model architecture and the Stochastic Gradient Descent (SGD) optimizer with an initial learning rate.
6.  **Defines the `ReduceLROnPlateau` callback:** Configures the callback to monitor the validation loss (`val_loss`), reduce the learning rate by a specified `factor` when no improvement is seen for a certain `patience` of epochs, and sets a minimum learning rate.
7.  **Trains the model:** Uses the `fit` method with the `ReduceLROnPlateau` callback.
8.  **Extracts learning rate history:** Manually tracks the learning rate at each epoch to plot it.
9.  **Identifies learning rate change points:** Determines the epochs where the learning rate was reduced.
10. **Generates plots:** Uses Matplotlib to create two subplots visualizing the learning rate schedule and the validation loss.

