# emo-classification-bilstm

<br/>
<br/>

## Introduction
In traditional neural networks, the information flows in one direction from input to output. However in RNNs, information is fed back into the system after each step. Which gives RNNs to allow the network to remember past information by feeding the output from one step into next step. This helps the network understand the context of what has already happened and make better predictions based on that. <br/>

![image](https://github.com/user-attachments/assets/573df663-5b47-4b1d-af16-9bddb1f054c0)

In this study, I wrote 2 RNN models: one from scratch (without any ML frameworks) and one with using [Tensorflow-Keras](https://www.tensorflow.org/guide/keras). The objective of this study is to determine the usefulness (if we need them or not) of ML frameworks on very small datasets.

<br/>
<br/>

## Methods
The dataset provided, which is `data.py`, has just 80 instances with very short sentences. There was no need to preprocess the data, as it was already clean and splitted for train/test. I just applied boolean to integer conversion for labels. After that, I tokenized the dataset using the [Keras-Tokenizer](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/text/Tokenizer) with a vocabulary size of 25.
Finally, I post-padded (padding=False) the input tokens to 15. This concludes the _Data_ part. <br/>
Now for the _Model_ part I defined 2 models with the following architectures:
1) **Scratch-RNN**: 1 hidden layer block with 128 hidden layers -> Dense layer with softmax activation. (lr = 2e-2, with SGD as the optimizer)
2) **Simple-RNN**: 1 hidden layer block (`SimpleRNN` from _Keras_) with 32 hidden layers -> Dropout layer with 0.3 -> Dense layer with softmax activation. (lr = 1e-3, with Adam as the optimizer)

<br/>
<br/>

## Results
Scratch-RNN    | Simple-RNN
:-------------------------:|:-------------------------:
![download](https://github.com/user-attachments/assets/04291961-d272-4a93-9f52-37c5537cb818) | ![download](https://github.com/user-attachments/assets/506cff4d-b2bd-4706-a7a3-aa3864b9711d)

| Model | Last Train Loss | Last Test Loss |
|--|--|--|
| Scratch-RNN | 0.009 | 0.009 
| Simple-RNN | 0.3616 | 0.4663 

<br/>
<br/>

## Discussions

