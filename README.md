# emo-classification-bilstm

<br/>
<br/>

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

This bidirectional nature of BiLSTMs makes them particularly effective for tasks where understanding both fast and future context is crucial. To demonstrate it's capabilities, I built 2 emotion classifiers: one is a RNN network build from scratch, and the other is a BiLSTM network using *TensorFlow*. <br/>
*I was not able to implement BiLSTM from scratch because it requires heavy math + backprop through time*

<br/>
<br/>

## Methods
The dataset provided, which is `data.py`, has just 80 instances. And wi
After that, I crated the RNN model with 2 hidden layer blocks with the size of 128. BiLSTM also has a size of 128, but it has 3 layers.
I trained the RNN for 500 epochs due to it's non-framework nature, and BiLSTM for just 10 epochs

<br/>
<br/>

## Results
![download](https://github.com/user-attachments/assets/710db508-1f05-4f1c-bb23-d7d3a7552272)
![image](https://github.com/user-attachments/assets/c0899c60-5e6e-4911-b4fd-c3191d3360d4)

