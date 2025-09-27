# Conv2dModelForNumbers <br>
Hello, everyone! It is nice to complete this simple project to practice basics of Convolutional Neural Networks. Here I want to describe the workflow of the project and the project itself.

**Data**: <br>
https://www.kaggle.com/datasets/olafkrastovski/handwritten-digits-0-9
I took the data from the Kaggle, and thanks to ANDRÉ MEIER for uploading this data there.

**Libraries**: <br>
I listed all libraries and their versions in the notebook. It is basic set of numpy, pandas, scikit-learn, and pytorch as well.
<hr>

**Workflow**: <br>
It wasn't so hard to work on the data, because it was in a good format, and well-organizer. However, I did some transformations.

*1. Transformations* <br>
I decided to change the size of the images to 224*224, since after I will be using MaxPool feature, and I need square-sized images for this purpose. I also thought, it would be easier to train the model, if we switch all images just to the gray mode. Some of images were written with blue pen, and some with black. It doesn't make any sense to assess this data from RGB perspective, because it doesn't give us any additional information. That's why I converted them to gray. After, we, of course, converted them to tensors as well as normalized them. Before the data contained different numbers, and I wanted to bring the mean to 0 and standard deviation to 1. It would allow the model easily train on this data. For that purpose, I first transformed data with no normalization, calculated mean and standard deviation, and only after used Normalize funciton in python.

*2. Data loader and division* <br>
I did not experimented here. Divided data as usual: 20% for training and 80% for validation. I used DataLoader function, and also divided the data to bathces, such that one branch would have 32 images.

*3. Model building* <br>
To build the model, I used seuqnetial model in python. First layers would repeadetly find patterns in data and pool this data to make it smaller and prevent overfitting. After, we flatten the data, and I used to layers of Linear computation along with Dropout layers to create the final result.

*4. Data training* <br>
To train the data, I used Adam optimizer and CrossEntropyLoss function to calculate the loss. The model would make prediction, after the loss function would be calculated. By backpropagation, we would adjust weights and biases. I trained model for 8 epochs, which I think was pretty enough, since it wasn't the hardest to work on the hand-written digits.

*5. Model's accuracy* <br>
Model showed 96.5% accuracy on the validation set which I regard as a good result. To convert model's results to something understandable, I used SoftMax along with Aggmax function

*6. My own test of the model* <br>
I asked my mom to write the number 8 on the paper using market and send the photo, which you can see in the notebook. The model, however was 77% sure that this was the number 6.
Then, I tried writing the number 8 on my IPad and checked this image. Now, the model was 99% sure it is a number 8.
I think, from here we can infer that the model is not ready for changes in thickness of the number as well as it cannot fully work with data when the background is not purely white. I am sure it is mostly because when converting to gray the darker the white background, more noise the data have, and, thus, cannot successfully identify the number.

**Conclusion** <br>
It was a great way to test my knowledge and make first steps towards Computer vision and image recognition, now we can move on to other projects.

