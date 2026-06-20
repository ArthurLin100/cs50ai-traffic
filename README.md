# gtsrb
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
 - Use 5x5 filters in the conv layer
#### Result
333/333 - 2s - 7ms/step - accuracy: 0.9695 - loss: 0.1414

## Size of 3x3 Pooling
#### Model Architecture
 - Use 3x3 pooling after the conv layer
#### Result
333/333 - 1s - 4ms/step - accuracy: 0.9632 - loss: 0.1616

## Size of 9x9 Pooling
#### Model Architecture
 - Use 9x9 pooling after the conv layer
#### Result
333/333 - 2s - 7ms/step - accuracy: 0.9609 - loss: 0.1617

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


# gtsrb-small

