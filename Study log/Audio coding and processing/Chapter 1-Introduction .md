## Introduction to Audio Processing and Coding 

### Audio coder attributes

对一个感知音频编码器主要从以下几个维度去评价，我们的目标是获得以低比特（<32kbit/s），可接受的算法延迟（5～20ms)以及更低的计算复杂度（1～10MIPS）

+ Audio quality 

  音频质量的传统衡量方法有SNR，total harmonic distortion (THD),为更好的评价，引入了其他客观和主观指标

+ Bite rates

  更低的比特率意味着更高的压缩率，和一定意义上的质量损失，如何在低比特率下传输相对较高的音频

+ Complexity 

  更低的计算复杂度，一般意味着更低的能量消耗和实时的处理效率，越低的计算复杂度，延时越低

+ Codec Delay

  音频语音编解码的延迟，对声音体验有较大的影响，就VoIP 应用，理想的编码解码延迟在5ms 

+ Error Robustness 

  流媒体，广播，直播等场景不断变化对对抗时变噪声提出了更高的要求

### Types of audio coders 

基于信号模型和信号的分析与合成，大致分为以下几类

+ Linear predictive 
+ Transform 
+ Subband 
+ Sinusoidal

音频编码算法也可以分为以下几类

+ 无损的音频编码
+ 有损的音频编码
