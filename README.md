# RNN_Learn
初次接触Attention模型的时候很是糊涂，根本分不清楚具体怎么回事。为了以后能够不再迷惑，现在把自己的理解写下来。
## 问题1：Attention中的Q,K,V是指什么？
Q是query的缩写，K是key的缩写，V是value的缩写。Query指的是当输出一个概率分布时，基于该概率分布进行查询，找寻最应该注意的点，实际上也相当于在翻译的时候，我们知道一个output的概率分布，去寻找这个词最应该和输入的哪个词最有联系，也就是更应该关注哪个点。Key和value都是来自于encoder，Key指的是Encoder端的输入的souce在隐藏层中的表达。我们可以想象，在RNN的单元GRU或LSTM中，每个输入的隐藏层和该输入的关系最密切，也就是该输入最能够影响这个隐藏值。而Q则指的是encoder输出的值，也可以理解为decoder的隐藏层。
## Attention常见图
![Image text](https://github.com/Wfast/RNN_Learn/blob/main/Attention_images/attention.PNG)
<img src="https://github.com/Wfast/RNN_Learn/blob/main/Attention_images/Easy_Attention.jpeg" style="transform:rotate(270deg);">
## Attention计算公式
![Image text](https://github.com/Wfast/RNN_Learn/blob/main/Attention_images/Compute.PNG)

这里有必要解释一下相应符号所代表的意思。
C<sub>i所代表的就是一个含有上下文所有信息的向量，同时根据注意力模型的性质，更加注意与之相对应的输入Vector。
a<sub>i,j代表了每个输入隐藏层的权重的比重，当然softmax函数是使强的更强，弱的更弱。
e<sub>ij所代表的就是decoder上个隐藏层输出和输入隐藏层的点积。
## self-attention
   self-attention,就是一个向量乘以它的转职。对于词的Embeding Vector来讲，就是每个词与其他词的关系。也成为协方差矩阵。
   
