# Summary
## Conv Layer Observation
 - Critical Impact: The convolutional layer is the core mechanism for spatial feature extraction. Completely removing both conv and pooling layers (Without Conv and Pooling) causes accuracy to plummet to 56.87%. Even removing just the conv layer (Without Conv Layer) yields a poor accuracy of only 65.69%.
 - Layer Stacking: Adding a second set of conv and pooling layers (2 Conv and Pooling Layer) yields the best performance overall, boosting accuracy to 98.21% and minimizing loss to 0.0777. This proves that a deeper convolutional structure extracts high-level features much more effectively.
## Pooling Layer Observation
 - Computational Efficiency: Removing the pooling layer (Without Pooling Layer) still maintains a decent accuracy of 96.08%, but the training time per step increases significantly (from the default 6ms/step to 10ms/step).
 - Conclusion: The primary benefit of the pooling layer is downsampling, which reduces feature map dimensions and computational load. This significantly speeds up training without sacrificing accuracy.
## Filter Number Observation
 - Positive Correlation: Model capacity scales with the number of filters. Doubling the filters to 64 improves accuracy to 97.53%.
 - Trade-off: Halving the filters progressively down to 16, 8, and 4 causes accuracy to drop (down to 95.09%) and loss to rise. However, fewer filters (16 or fewer) cut step time in half from 6ms to 3ms, making it a viable trade-off for resource-constrained environments.
## Filter Size Observation
 - Receptive Field: Increasing the filter size to 5x5 expands the local receptive field, slightly improving accuracy to 97.69% while maintaining a fast training speed (4ms/step).
 - Diminishing Returns: The data shows that excessively large filters increase step time to 7ms/step and cause accuracy to drop (96.95%) compared to the 5x5 baseline, indicating that overly large kernels introduce noise and unnecessary computational overhead.
## Pooling Size Observation
 - Size Impact: Enlarging the pooling window from 2x2 to 3x3, 5x5 or 9x9 leads to a decline in accuracy (from 96.86% down to 76.24%) and elevates the loss to 0.7996.
 - Conclusion: Oversized pooling windows cause severe information loss (feature dilution) during downsampling. Sticking to a standard 2x2 pool size remains the safest and most effective choice.
## Hidden Layer Number Observation
 - Overfitting & Optimization Difficulty: Deepening the network to 5 hidden layers decreases accuracy to 94.20% and increases loss to 0.2242.
 - Conclusion: Blindly adding fully connected layers does not benefit this specific dataset. Instead, it increases parameter complexity, which can lead to vanishing gradients or overfitting. Deeper is not always better.
## Dropout Observation
 - The Cost of Imbalance: Setting the Dropout rate to an extreme 0.9 forces the network to lose 90% of its neurons during training, resulting in severe underfitting and a massive accuracy drop to 63.26%.
 - Mild Regularization: Lowering Dropout to 0.1 yields an accuracy of 96.88%, which is highly comparable to the default 0.5 (96.82%). While a moderate Dropout range (0.1 to 0.5) keeps performance stable, an excessively high rate hurts the network's capacity to learn.

# Test Details
## Default
#### Model Architecture
- Convolutional layer: 32 filters, 3×3 kernel, ReLU activation
- Max-pooling layer: 2×2 pool size
- Dense hidden layer: 128 neurons, ReLU activation
- Dropout: 0.5
- Output layer: 3 neurons, Softmax activation
#### Result
333/333 - 2s - 6ms/step - accuracy: 0.9682 - loss: 0.1253  

## Without Conv and Pooling Layer
#### Model Architecture
 - Remove conv and pooling layer from the default architecture 
#### Result
333/333 - 1s - 5ms/step - accuracy: 0.5687 - loss: 1.4576

## Without Pooling Layer
#### Model Architecture
 - Remove pooling layer from the default architecture 
#### Result
333/333 - 3s - 10ms/step - accuracy: 0.9608 - loss: 0.1510

## Without Conv Layer
#### Model Architecture
 - Remove conv layer from the default architecture 
#### Result
333/333 - 1s - 3ms/step - accuracy: 0.6569 - loss: 1.3468

## 2 Conv and Pooling Layer
#### Model Architecture
 - Add another set of conv and pooling layer from the default architecture 
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.9821 - loss: 0.0777

## Doubled Filter Numbers
#### Model Architecture
 - Use 64 filters in the conv layer
#### Result
333/333 - 2s - 6ms/step - accuracy: 0.9753 - loss: 0.1118

## 1/2 Filter Numbers
#### Model Architecture
 - Use 16 filters in the conv layer
#### Result
333/333 - 1s - 3ms/step - accuracy: 0.9699 - loss: 0.1210

## 1/4 Filter Numbers
#### Model Architecture
 - Use 8 filters in the conv layer
#### Result
333/333 - 1s - 3ms/step - accuracy: 0.9611 - loss: 0.1708

## 1/8 Filter Numbers
#### Model Architecture
 - Use 4 filters in the conv layer
#### Result
333/333 - 1s - 3ms/step - accuracy: 0.9509 - loss: 0.1982

## Size of 5x5 Filter
#### Model Architecture
 - Use 5x5 filters in the conv layer
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.9769 - loss: 0.1084

## Size of 9x9 Filter
#### Model Architecture
 - Use 9x9 filters in the conv layer
#### Result
333/333 - 2s - 7ms/step - accuracy: 0.9695 - loss: 0.1414

## Size of 3x3 Pooling
#### Model Architecture
 - Use 3x3 pooling after the conv layer
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.9632 - loss: 0.1616

## Size of 5x5 Pooling
#### Model Architecture
 - Use 5x5 pooling after the conv layer
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.9312 - loss: 0.2731

## Size of 9x9 Pooling
#### Model Architecture
 - Use 9x9 pooling after the conv layer
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.7624 - loss: 0.7996

## 5 Hidden Layers
#### Model Architecture
 - Use 5 hiden layers with 1 dropout in the last hidden layer
#### Result
333/333 - 2s - 5ms/step - accuracy: 0.9420 - loss: 0.2242

## Dropout 0.9
#### Model Architecture
 - Use 0.9 Dropout
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.6326 - loss: 1.3835

## Dropout 0.1
#### Model Architecture
 - Use 0.1 Dropout
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.9688 - loss: 0.1342

