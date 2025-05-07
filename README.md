# Sentiment Analysis with RNNs

<br/>
<br/>

## Introduction
In traditional neural networks, the information flows in one direction from input to output. However in RNNs, information is fed back into the system after each step. Which gives RNNs to allow the network to remember past information by feeding the output from one step into next step. This helps the network understand the context of what has already happened and make better predictions based on that. <br/>
Here are the key components of RNN based models:
- **Recurrent Neurons:** Fundamental processing unit in RNN. Recurrent units hold a hidden state that maintains information about previous inputs in a sequence.
- **RNN Unfolding:** Process of expanding the recurrent structure over time steps. During unfolding each step of the sequence is represented as a separate layer in a series illustrating how information flows across each time step.

This unrolling enables backpropagation through time (BPTT) a learning process where errors are propagated across time steps to adjust the network’s weights


![image](https://github.com/user-attachments/assets/573df663-5b47-4b1d-af16-9bddb1f054c0)

Here are the key components of RNN architecture:
- **Recurrent Neurons:** The fundamental processing unit in RNN is a Recurrent Unit. Recurrent units hold a hidden state that maintains information about previous inputs in a sequence. 
- **RNN Unfolding:** RNN unfolding or unrolling is the process of expanding the recurrent structure over time steps. This unrolling enables backpropagation through time (BPTT) a learning process where errors are propagated across time steps to adjust the network’s weights.

In this study, I wrote 2 RNN models: one from scratch (without any ML frameworks) and one with using [Tensorflow-Keras](https://www.tensorflow.org/guide/keras). The objective of this study is to determine the usefulness (if we need them or not) of ML frameworks on very small datasets.

<br/>
<br/>

## Methods
The dataset provided, which is `data.py`, has just 80 instances with very short sentences. There was no need to preprocess the data (besides tokenization), as it was already clean and splitted for train/test. I just applied boolean to integer conversion for labels. After that, I tokenized the dataset using the [Keras-Tokenizer](https://www.tensorflow.org/api_docs/python/tf/keras/preprocessing/text/Tokenizer) with a vocabulary size of 25.
Finally, I post-padded (padding=False) the input tokens to 15. This concludes the _Data_ part. <br/>
Now for the _Model_ part I defined 2 models with the following architectures:
1) **Scratch-RNN**: 1 hidden layer block with 128 hidden layers -> Dense layer with softmax activation. (lr = 2e-2, with SGD as the optimizer)
2) **Simple-RNN**: 1 hidden layer block (`SimpleRNN` from _Keras_) with 32 hidden layers -> Dropout layer with 0.3 -> Dense layer with softmax activation. (lr = 1e-3, with Adam as the optimizer)
I trained _Scratch-RNN_ for 500 epochs and _Simple-RNN_ for 10 epochs. The logic behind this gap is that I expected _Simple-RNN_ to be more stable.

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
Performance of _Scratch-RNN_ was off the charts, with nearly 1.00 accuracy on both train and test splits. However,_Simple-RNN_ performed slightly worse compared to it's counterpart with a maximum accuracy of 0.85 on test set and a possible overfit problem on the last 100-200 epochs. It should be noted that without the Dropout layer, _Simple-RNN_ had an accuracy decrease of 10-20%, so to compare both models effectively I choose the latter model. <br/>
In my opinion the fact that my _Simple-RNN_ model performed worse because it has a relatively complex architecture for the dataset. In other words, dataset is to "perfect" for such a deep network. Other possible reasons may include:
- Gap Between Number of Epochs (500 vs 10)
- Tokenization Algorithms
- Gradient Vanishing
- Activation Functions

Further experimentation is required to inspect these solutions. One possible solution is to perform batch normalization to prevent gradient vanishing. But for this study alone, I can colclude that using ML frameworks are not necessary for clean and small datasets.

<br/>
<br/>

### Resources
- [Introduction to RNNs](https://www.geeksforgeeks.org/introduction-to-recurrent-neural-network/)
- [rnn-from-scratch](https://github.com/vzhou842/rnn-from-scratch)
