# Cheatsheet Tensorflow
## Interesting links
#### Machine Learning Crash Course
https://developers.google.com/machine-learning/crash-course
#### Basic Image Classification
https://www.tensorflow.org/tutorials/keras/classification?hl=nl
#### Image loading and preprocessing
https://www.tensorflow.org/tutorials/load_data/images
#### Linear Regression, Logistic Regression, Softmax Regression
http://ufldl.stanford.edu/tutorial/supervised/LinearRegression/
#### Image dataset


## Important Terminology
| Word                                                    | Terminology                                                                                                                                               | Example                                                                                                                                              |
| ------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Label                                                   | `This is what we are trying to predict. In linear regression this is the y variable. `                                                                    | We want to predict a win or loss for a specific boxer. The chance the boxer will win OR lose (depending on declaration of variable) is the label     |
| Feature                                                 | `This is a variable we will use to try and predict the Label. This is the input, described as x in linear regression. There can be millions of features.` | The history of won fights can be used as input to predict the outcome of a match. The history is a feature.                                          |
| Example                                                 | `Particular instance of data`                                                                                                                             | 2 categories: labeled and unlabeled                                                                                                                  |
| Labeled Example                                         | `This is used to train the model. This contains feature(s) and Label`                                                                                     | Here you have the label to check if the model predicted correctly: <br>{features, label}: (x,y)                                                      |
| Unlabeled Example                                       | `This is used on a trained model to make predictions`                                                                                                     | There is no outcome to check if the prediction is correct. This is therefor used when the model is sufficiently trained.<br>{features, ?}: (x,?)     |
| Supervised Machine Learning                             | `Uses labeled examples to train the model`                                                                                                                |                                                                                                                                                      |
| Model                                                   | `This defines the relationship between features and labels. (true?: With the use of weights per feature.)`                                                | Two phases: <br>Training: give the model labeled examples.<br>y' = b + w1*x1 + w2*x2 ... + wn*xn                                                     |
| Inference                                               | `give the model unlabeled examples to try to predict the label (y)`                                                                                       |                                                                                                                                                      |
| Regression                                              | `Predicts continuous values.`                                                                                                                             | Predicts value of a house, chance that a boxer will win.                                                                                             |
| Classification                                          | `Predicts discrete values.`                                                                                                                               | Predicts if the image shows a dog or cat.                                                                                                            |
| Loss                                                    | `Loss is a number indicating how bad a prediction was on a single example.`                                                                               |                                                                                                                                                      |
| Empirical Risk Minimization                             | `Try to find the model that mimimizes loss`                                                                                                               |                                                                                                                                                      |
| Loss function                                           | `This is a function that calculates how much loss there is with the prediction of the model.`                                                             |
| Squared Loss                                            | `This is the loss squared for a single example`                                                                                                           |                                                                                                                                                      |
| Mean Square Error (MSE)                                 | `The mean of all losses in a dataset`                                                                                                                     | MSE = 1 / N * sum(y - prediction(x))^2                                                                                                               |
| Converged                                               | `The model has converged when the overall loss stops changing or changes extremely slowly after many iterations`                                          | Iteration:<br>prediction -> compute loss -> parameter update                                                                                         |
| Gradient Descent                                        | `Way to find convergence point and reduce loss to a minimum`                                                                                              | ![Gradient Descent](../LearningTensorflow/Images/GradientDescent.png)                                                                                |
| Learning Rate                                           | `How big are the steps taken on the curve.`                                                                                                               | Too small => takes forever<br>Too large => overshoots                                                                                                |
| Gradient                                                | `Equals the derivative with one weight? More weights the gradient becomes a vector.`                                                                      |                                                                                                                                                      |
| Batch                                                   | `A batch is the total number of examples you use to calculate the gradient in a single iteration.`                                                        | Not all examples of the dataset are always used, because it can take to long and too much computation in one iteration.                              |
| Stochastic gradient descent = SGD                       | `Uses a single chosen at random example to calculate the gradient`                                                                                        |                                                                                                                                                      |
| Mini-batch stochastic gradient descent = Mini-batch SGD | `Uses 10 to 1000 examples`                                                                                                                                |                                                                                                                                                      |
| Epoch                                                   | `In one epoch every example from a dataset can be processed`                                                                                              | If the batch has all the examples, one epoch has one iteration. If the batch contains only half of the examples, one epoch will have two iterations. |
| Overfitting                                             | `When a model fits too well with the training data, but doesn't have good predictions for new data. It does not generalize well to new data.`             | The model overfits peculiarities in the trained data.<br>Tension in ML: fitting data well as simply as possible. Less complexity is beter.           |
| Generalization                                          | `Your model predicts new data pretty well.`                                                                                                               | Three assumptions: <br><ol><li>Independently and identically</li><li>Stationary</li><li>Same distribution</li></ol>                                  |
| Training Set                                            | `Dataset to train your model`                                                                                                                             | Like exercises to practise for the exam.                                                                                                             |
| Test Set                                                | `Dataset to test your best trained model according to Validation Set.`| Like the exam after you practised.<br>Conditions for a good test set:<ul><li>Large enough</li><li>Representative</li></ul>|
| Validation Set | `After one iteration of training, this dataset evaluates the results from the model.` | Tweaking of the model happens according to results on Validation Set |
|Feature Engineering | `Transforming raw incoming data to a feature vector.`| Raw data can for example be given in json format. Strings will be converted to a floating-point value. For this you can use a vocabulary. |
|Feature Vector| `A set of floating-point values comprising the examples in your data set`|  |
| Vocabulary | `A collection that maps every category to a numeric value or a position on a vector.` |  |
| One-hot encoding | `A string feature is mapped on a binary vector where only one element has the value 1 (true)` | [0,0,0,0,0,1,0,0,0] |
| Multi-hot encoding | `A string feature is mapped on a binary vector where multiple elements have the value 1 (true)` | [0,0,0,0,0,1,0,1,0] |
|Scaling | `Converting floating-point features to standard range.` | [0 : 1 ] <br>[-1 : 1 ]|
| Feature Crossing | `Is a synthetic feature formed by multiplying (crossing) two or more features (mostly one-hot feature vectors). This is very efficient for large data sets. The result is a float or a vector with every possible combination.` | [A x B]<br>[A x B x C x D]<br>[A x A]<br> |
| bucket / bin | `A range of values is taken together in a bucket/bin.` | latitude and longitude as float is not a good predicter for housevalue. Therefor it is better to group them together in buckets/bins per neighbourhood. |
| Regularization | `Penalize models that are too complex and result in overfitting.` | You will minimize loss AND complexity. This is called structural risk minimization:<br>minimize(Loss(Data<>Model) + Complexity(Model)) |
| Loss term and regularization term | `Respectively these indicate how well the model fits the data and how much complexity there is in the model.` | This is used in the function that is a training optimization algorithm. |
| Regularization function/ formula | `This is the sum of the squared weights per feature. In this case the weight indicates the complexity of a feature.` | reg = (w1)^2 +  (w2)^2 + ... + (wn)^2 | 
| Lambda | `Regularization strength. Too high => Model too simple. Too low => Model too complex.` | minimize(Loss(Data<>Model) + lambda * Complexity(Model)) |
| ROI | `Region Of Interest` |  |
| Layer | `Layers exstract representations from the data.` | |
| Dense Layer | `Dense layer is the regular deeply connected neural network layer. It is most common and frequently used layer. Dense layer does the below operation on the input and return the output.` | |
| Convolutional Network | `Consists of three main types of layers: Convolutional layer, pooling layer, fully-connected layer` | This network is often used in image classification. |
| Convolutional layer | `This layer has an amount of feature detectors (a.k.a. kernels/filters) which will move over the image to detect if a cetain feature is present` |  |
| Pooling layer | `` | Maxpooling, minpooling. |
| Convolution | `Checking if a feature is present` | See convolutional layer |
| feature detector | `Is often a 2d array of weights which moves over the image. On every position this calculates the dot product. The result is stashed in an output array called the feature map` | This is also called a filter or kernel. Kernel size refers to the size of the filter moving over the image. |
| Feature map | `Result of the convolutional layer` | This is also called the activation map or convolved feature. |
| Masking | `The simplest form is to hide or show certain parts of the picture.` | In segmentation these are the colors that are used to categorize the pixels to a class. |
| U-Net | `Consists of an encoder (downsampler) and a decoder (downsampler).` | MobileNetV2 is an example of a encoder. <br>pix2pix (upsample block) is an example of a decoder. |
| Multichannel feature map |  | Zie feature map. |
| Activation Function| `This is the function calculating per 'neuron' a value that will determine if the neuron 'activates' or not OR how much the neuron activates. It has multiple input values (x) which are weighted (w).` | ReLU is an example of this. Also the sigmoid activation function is one. |
| Rectified Linear Unit (ReLU) | `f(x) = max(0,x)`<br> `This will generate an output from zero to infinite.` | This function is very simple and doesn't require much computing power. It is also very good to create a sparse network. Downside is that it can eliminate the influence of certain neurons. |
| Sparse Network | `Network/matrix with some zeros indicating that some features are abscent.` | This is efficient because some features will not be included in the next layer. |
| Leaky ReLU | `f(x) = max(0.01*x, x)`| This addresses the problem of eliminating neurons (dying ReLU). |
| Feature Channel | `An image has three channels: RGB. Filters are executed on one of these channels. ` | https://ai.stackexchange.com/questions/5769/in-a-cnn-does-each-new-filter-have-different-weights-for-each-input-channel-or |
| Logit | Vector of raw predictions that a model generates ||

## Code
### TensorFlow and Keras
| code | explanation| example|
| --------------------- | ----------------------- | --------- |
| tf.keras.datasets     | gets the given dataset to train your AI on. <br>In the example this is the mnist dataset. | `tf.keras.datasets.mnist` |
| [dataset].load_data() | I think this loads in the data from the dataset | `mnist.load_data()`|
| tf.feature_column.* | | |
| tf.keras.regularizers.l2() | Used to add regularization on a layer to reduce the overfitting. For example it is given as a parameter in a layer in the creation of the model | `kernel_regularizer=tf.keras.regularizers.l2(0.001)` |
| tf.keras.functional.Functional | Is a flexibel API to create a model. The API gives the possibility to handle a non-linear topology which the Sequential API cannot. | `tf.keras.Model(inputs=inputs, outputs=outputs)` |


### PIL/Pillow
| code                  | explanation                                                                                | example                          |
| --------------------- | ------------------------------------------------------------------------------------------ | -------------------------------- |
| from PIL import Image | Imports the right library to be able to view images with python                            | `from PIL import Image as im`    |
| im.fromarray()        | Creates an image memory (Pillow image) from an array                                       | `image = im.fromarray(imageArr)` |
| im.open()             | Opens and identifies an image file, but doesn't read it (lazy) until you try to process it | `image = im.open("./Images/rose")`              |
| image.show()          | Shows the image that is assigned tp the variable image                                     | `image.show()`                   |

### pathlib
| code| explanation| example|
| --- | --- | --- |
| dir.glob() | Collect all files in path that corresponds with regex | `dir.glob('*/*.jpg')` |
