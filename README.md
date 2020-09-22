# Image-Captioning
Image caption generation is the task of generating a natural language description of the content of an image.
I have used a concept of transfer learning for extracting Image features and Learning the Word Embeddings.
Transfer Learning Models used:
1. IncetionV3 (Extract Image Features)
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
15. Generation: Greedy Search and Beam Search of width 3


In Merge Achitecture rather than combining image features together with linguistic features from within the RNN, merge architectures delay their combination until after the caption prefix has been vectorised. Model can be visualised by file model.png. However comparative studies by Marc Tanti has showed that merge model tends to perform better than the inject model. Although various modifications have been introduced in inject model(pre-inject, par-inject, post-inject and init-inject) and merge model(merge-concat, merge-add and merge-mult), I have implemented merge-add architecture.
