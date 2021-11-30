# TWICE-Face-Recognition-Classifier
## A face recognition classifier of a K-Pop group members using neural networks

This is a face recognition project heavily based on Jason Brownlee's [tutorial](https://machinelearningmastery.com/how-to-develop-a-face-recognition-system-using-facenet-in-keras-and-an-svm-classifier/) using pictures I have collected. None of these pictures belong to me; they belong to each of their respectful owners. 

First each of the picture in each class is scanned for a face to be detected and extracted using Multi-Task Cascaded Convolutional Neural Network, or ([MTCNN](https://github.com/ipazc/mtcnn)), implementation provided by Iván de Paz Centeno, according to tutorial. Then, using the Keras FaceNet pretrained model, provided by [Hiroki Taniai](https://github.com/nyoki-mtl/keras-facenet), each extracted face is embedded and standardized. Finally the dataset is fed into a Dense neural network. Multiple network configurations are used to train the dataset, with the highest validation accuracy reaching ____%.

