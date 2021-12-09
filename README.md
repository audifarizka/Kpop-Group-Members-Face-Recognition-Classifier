# Kpop-Group-Members-Face-Recognition-Classifier

## A face recognition classifier of a K-Pop group members using neural networks


This is a face recognition project heavily based on Jason Brownlee's [tutorial](https://machinelearningmastery.com/how-to-develop-a-face-recognition-system-using-facenet-in-keras-and-an-svm-classifier/) using pictures I privately collected. None of these pictures belong to me; they belong to each of their respectful owners. 

First each of the picture in each class is scanned for a face to be detected and extracted using Multi-Task Cascaded Convolutional Neural Network, or ([MTCNN](https://github.com/ipazc/mtcnn)), implementation provided by Iván de Paz Centeno, according to tutorial. Then, using the Keras FaceNet pretrained model, provided by [Hiroki Taniai](https://github.com/nyoki-mtl/keras-facenet), each extracted face is embedded and standardized. Finally the dataset is fed into a Dense neural network. Multiple network configurations are used to train the dataset, with the highest validation accuracy reaching 95.4%.

## 1. Data 

The data is a collection of pictures of the member's of the group privately collected as a hobby of me being a fan. They are mainly posted on their social medias, such as their official Twitter account, and from photographers, which, none of those belong to me. The pictures are manually selected with few criterias that suit the code:

  1. The picture can only contain one member only. Collages are not acceptable, either.
  2. The member's face has to face the camera without having too many angles.
  3. The pictures are not close-up shots of the member.
  4. The pictures are well lit and must contain as minimal filter as possible.

Example of unacceptable pictures:

![IMG_7104](https://user-images.githubusercontent.com/58354284/144191135-54dc1c8b-b01c-47c8-b3ed-e8f2e9ba6b1c.JPG)

Example of acceptable pictures:

![IMG_6105](https://user-images.githubusercontent.com/58354284/144191510-3eabf4b9-2be9-44a8-bee9-d3f3f852ad02.JPG)

(Both pictures are from the official twitter [account](https://twitter.com/JYPETWICE))


Some pictures show members going through the airport in which they usually wear a face mask. These pictures wont get detected, however a picture of members wearing shades can be detected. Other pictures may show members standing in a crowd, which will work if other faces in the pictures are blured. Each member's pictures are put into their own folder that will be their label/class.

## 2. Algorithm

First the each picture is scanned to look for the face. Then, a bounding box is created and the face within the box is extracted and put into an array. The original code by Jason Brownlee is using PIL library to operate with the image, but I took the liberty to tweak a little and use OpenCV, instead (which is also from his other face detection [tutorial](https://machinelearningmastery.com/how-to-perform-face-detection-with-classical-and-deep-learning-methods-in-python-with-keras/)).

Example of faces being detected by bounding box:

![Examples](https://user-images.githubusercontent.com/58354284/145341108-42117304-e957-47ae-a6ae-ef3e93be6512.png)

We can see there are various angles and expressions and lightings of the faces in the examples, including one with sunglasses on.

Since the process of loading the images take a long time and a lot of memory, each class of member was loaded one at a time and each picture folder is put into another folder (2-deep folder). After all the members are loaded, they are then combined and compressed into one single file consists of X and y arrays for easy loading in the future. After the data is split into train and validation set, the face embedding is created for each face for both set. Both data are normalized after being fit to the training data and the label data are encoded. The same treatment is done to the test set as well.

## 3. Model

Several neural network sequential models are created, with each having more neurons and/or layers but also with more regularization methods. Both model_5 and model_6 achieved 95.4% validation accuracy score (model_6 reached lower validation loss score of 25.3%). Each model has also different optimizer function, also with different parameter settings.

![model_6_plots](https://user-images.githubusercontent.com/58354284/144190281-a2abfe16-4f0f-411b-acee-1d8d6dd177ca.png)

## 4. Results

The results of model_6 to the test data are shown below. The pictures were plotted randomly with the predicted labels as their titles. Among them, only one face was wrongly recognized (circled). However, results may vary about which member gets wrong result.

![Results](https://user-images.githubusercontent.com/58354284/144177606-203f9ebb-c9ee-4345-a42e-0ac96071f35a.png)



This models are run using NVIDIA GeForce RTX 2060 mobile
