# emo-classification-bilstm

## Introduction
In traditional neural networks, the information flows in one direction from input to output. However in RNNs, information is fed back into the system after each step. Which gives RNNs to allow the network to remember past information by feeding the output from one step into next step. This helps the network understand the context of what has already happened and make better predictions based on that. <br/>

![image](https://github.com/user-attachments/assets/573df663-5b47-4b1d-af16-9bddb1f054c0)

However, RNNs suffer from a common issue called _vanishing gradients_. The vanishing gradient problem is a challenge that emerges during backpropagation when the derivatives or slopes of the activation functions become progressively smaller as we move backward through the layers of a neural network. The weight updates becomes extremely tiny, or even exponentially small, it can significantly prolong the training time, and in the worst-case scenario, it can halt the training process altogether. <br/>

There are a number of ways to overcome this issue:
- Batch Normalization
- ReLU as Activation Function
- Skip Connections and Residual Networks (ResNets)
- Long Short-Term Memory Networks (LSTMs) *
- Gated Recurrent Units (GRUs)

In this study, I tried to overcome the vanishing gradients problem by using an extension of the LSTM networks, namely BiLSTM (Bidirectional Long Short-Term Memory). BiLSTMs allow information to flow from both forward and backward, unlike their traiditional predecessor LSTMs which processes sequences in only one direction. BiLSTM's consists of two seperate LSTM layers:
- **Forward LSTM:** Processes the sequence from start to end
- **Backward LSTM:** Processes the sequence from end to start
<br/>

![image](https://github.com/user-attachments/assets/63638495-0d2f-441b-ad37-3b2fe4a25acf)

This bidirectional nature of BiLSTMs makes them particularly effective for tasks where understanding both fast and future context is crucial. To demonstrate it's capabilities, I built an emotion classifier, one of the most famous NLP tasks in literature.

<br/>
<br/>

## Methods
To demonstrate the power of BiLSTMs on larger datasets, I choose [Twitter Emotion Classification Dataset](https://www.kaggle.com/datasets/aadyasingh55/twitter-emotion-classification-dataset), which contains more than 400k instances with just 2 features:
- _text_: string feature representing the tweet.
- _label_: classification label with the following values:
  * 0 : sadness
  * 1 : joy
  * 2 : love
  * 3 : anger
  * 4 : fear
  * 5 : surprise


