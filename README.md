# Image-Captioning
Image caption generation is the task of generating a natural language description of the content of an image.
I have used a concept of transfer learning for extracting Image features and Learning the Word Embeddings.
Transfer Learning Models used:
1. InceptionV3 (Extract Image Features)
2. Glove6B.100d (100 dim Word Embedding)

Summary of All Configurations:
1. Dataset: Flicker8K
2. FrameWork: Keras with Tensorflow backend
3. Architecture: Merge Model(using add)
4. Model type: Encoder Decoder
5. Word Embedding: Glove (Pretrained 6B.100d)
6. RNN: LSTM
7. Vocabulary: All tokens appearing 10 times or more
8. Optimisation: Adam
9. Clipping Value: 3
10. Batch Size: 32
11. Regularisation: Dropout with dropout rate 0.5
12. Stopping Criteria: Early Stopping with a patience of 2 Epochs
13. Gradient Control: Gradient Clipping with value 3
14. Initialisation: biases-> zeros, feedforward weights-> xavier, recurrent weights-> orthogonal
15. Epochs: 30
16. Generation: Greedy Search and Beam Search of width 3

In Merge Achitecture rather than combining image features together with linguistic features from within the RNN, merge architectures delay their combination until after the caption prefix has been vectorised. Model can be visualised by file model.png. However comparative studies by Marc Tanti has showed that merge model tends to perform better than the inject model. Although various modifications have been introduced in inject model(pre-inject, par-inject, post-inject and init-inject) and merge model(merge-concat, merge-add and merge-mult), I have implemented merge-add architecture.

For Image dataset I have used Pretrained Inceptionv3(minus last 2 layers) which was performed on Imagenet to extract the image features.
Moreover Pretrained Glove Embeddings are used to reduce the training time of the model. It can be downloaded from https://github.com/stanfordnlp/GloVe

The dataset consist of 8,000 images that are each paired with five different captions which provide clear descriptions of the salient entities and events. The images were chosen from six different Flickr groups, and tend not to contain any well-known people or locations, but were manually selected to depict a variety of scenes and situations. The images are divided into train set (6000 images), validation set(1000 images), and test set (1000 images).

Dataset can be downloaded by filling in the request form https://forms.illinois.edu/sec/1713398.

If the above request form doesn't work you can download the data from here: https://academictorrents.com/details/9dea07ba660a722ae1008c4c8afdd303b6f6e53b or here: https://github.com/jbrownlee/Datasets/releases

Results:

Model reaches the bleu Score of 55% for unigrams on test set and 56% for training set. You can further improve the score by training the model for longer durations or using a more sophisticated RNN with more layers and using a larger dataset like flicker30 or MSCOCO. 

I have also shared the final weight of my trained model. Feel free to use it and save yourself from longer traning.
