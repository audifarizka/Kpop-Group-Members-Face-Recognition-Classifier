# TWICE-Face-Recognition-Classifier
## A face recognition classifier of a K-Pop group members using neural networks

This is a face recognition project heavily based on Jason Brownlee's [tutorial](https://machinelearningmastery.com/how-to-develop-a-face-recognition-system-using-facenet-in-keras-and-an-svm-classifier/) using pictures I have collected. None of these pictures belong to me; they belong to each of their respectful owners. 

First each of the picture in each class is scanned for a face to be detected and extracted using Multi-Task Cascaded Convolutional Neural Network, or ([MTCNN](https://github.com/ipazc/mtcnn)), implementation provided by Iván de Paz Centeno, according to tutorial. Then, using the Keras FaceNet pretrained model, provided by [Hiroki Taniai](https://github.com/nyoki-mtl/keras-facenet), each extracted face is embedded and standardized. Finally the dataset is fed into a Dense neural network. Multiple network configurations are used to train the dataset, with the highest validation accuracy reaching 95.4%.


This is the result using the model that reached highest validation accuracy score. The test pictures are taken from the official twitter account of the group. The pictures were plotted randomly with the predicted labels as their titles. Among them, only one face was wrongly recognized (circled). However, results may vary about which member gets wrong result.
![Results](https://user-images.githubusercontent.com/58354284/144177606-203f9ebb-c9ee-4345-a42e-0ac96071f35a.png)
