Name: Helena Mo
UNI: hm3194

1. One-hot encoding
One-hot encoding represents a label with one 1 and the rest 0s. I use to_categorical(labels, num_classes=25) to match my output layer and categorical cross-entropy loss.

2. Dropout
Dropout randomly sets some inputs to zero during training to help reduce overfitting. I use Dropout(0.3) after Flatten so the model does not depend too much on a few features.

3. ReLU and sigmoid
ReLU changes negative values to 0 and keeps positive values, while sigmoid maps values to between 0 and 1. Sigmoid can have very small gradients near its limits, so I use ReLU in my convolutional layers.

4. Softmax
Softmax turns output scores into probabilities that sum to 1. Since each image has one correct letter, my code uses argmax to select the most likely class.

5. Output sizes
The convolution output is 96 * 96 * 16 because (100 - 5) / 1 + 1 = 96. The max-pooling output is 48 * 48 * 16.

6. Validation and test accuracy
My validation accuracy was about 100%, higher than my test accuracy of 93.29%. Since train.csv contains augmented images, similar versions of an image may appear in both training and validation sets, making validation easier.

Model and workflow
I added a second convolutional layer after the simpler model scored below 90%. My final CNN uses 32 and 64 filters, max pooling, Flatten, Dropout(0.3), and 25 softmax outputs; I normalize pixels, use an 80/20 split, and train for 30 epochs with Adam and batch size 128.
