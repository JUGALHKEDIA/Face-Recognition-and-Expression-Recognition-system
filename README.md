# Face Recognition and Expression Recognition system

The Face Recognition and Expression recogntion system is combined as Face Recognition system and Expression/Emotion Recogntion system.

## Face Recognition system

Face recognition system mainly consists of 2 parts;

1. **Building dataset**  
Here I used Microsoft bing's image search API to build celebrity dataset. Given the list of celebrities to the API program and a parameter N (***number of images to obtain***) the program looks for Top N number of pictures of each celebrity. Checks for open-source licensing agreement for the images and stores them into a directory-file structure. A further human check on these directories is made since there may be redundant copies of celebrity photos or other kind of errors.

2. **Deep transfer matric learning**  
The advantages of using deep transfer matric learning is that it the pretrained model is highly accurate and saves a lot of training time as compared to when trying to train the model from scratch. 

Instead of trying to output single label(or even the cordinates/bounding box region of objects in an image), with the help of Deep transfer matric learning model we are instead outputting a real-valued feature vector.

For the face-recognition (dLib) network, the output feature vector is **128-dimensional** (i.e., a list of 128 real-valued numbers) that is used to quantify the face. The Training the network is done using **triplet** function.

<img src="https://github.com/JUGALHKEDIA/Face-Recognition-and-Expression-Recognition-system/blob/main/face_recognition_opencv_triplet.jpg" alt="face_recognition_triplet" style="width:80%"> 


Here we provide three images to the network; Two of these images are example faces of the same person. The third image is a random face from our dataset and is not the same person as the other two images.

Our network quantifies the faces, constructing the 128-d embedding (quantification) for each. From there, the general idea is that we’ll tweak the weights of our neural network so that the 128-d measurements of the two Will Ferrel will be closer to each other and farther from the measurements for Chad Smith. Our network architecture for face recognition is based on ResNet-34 from the [Deep Residual Learning for Image Recognition](https://arxiv.org/abs/1512.03385#) paper by He et al., but with fewer layers and the number of filters reduced by half.

The network itself was trained by Davis King on a dataset of ≈3 million images. On the [Labeled Faces in the Wild (LFW)](http://vis-www.cs.umass.edu/lfw/) dataset the network compares to other state-of-the-art methods, reaching 99.38% accuracy.


## Expression Recognition system.

For the purpose of expression/emotion recognition we are using [FER dataset](https://www.kaggle.com/datasets/msambare/fer2013) which consists of images of faces of size (48 x 48 pixel). The dataset consists of 28,709 training examples and 3,589 test set examples.

*Example: running the model on some test images*

<img src="https://github.com/JUGALHKEDIA/Face-Recognition-and-Expression-Recognition-system/blob/main/face_expression.gif" alt="example of face expression recognition" style="width:75%">