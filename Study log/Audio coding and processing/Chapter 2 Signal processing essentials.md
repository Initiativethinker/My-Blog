## Signal Processing Essentials

### STFT-短时傅里叶变换

![image-20191119142046391](/Users/mac/Library/Application Support/typora-user-images/image-20191119142046391.png)

STFT相当于取一个滑动窗口内的一个傅立叶变换，它有两种解释方式：

+ 当n 固定，可以当作是w(n-m)x(m) (-∞<m<∞) 的傅立叶变换
+ 当w固定，窗函数w(n)卷积信号![image-20191119142651015](/Users/mac/Library/Application Support/typora-user-images/image-20191119142651015.png)

####窗的选取对STFT的影响

+ 窗的长度选取与时域和频域分辨率的关系

  **在STFT中，时域和频域的采样点是相同的，如果窗长越长，意味着选取的片段越长，信号越宽，时域分辨率就越低**

  **在频域中，信号越宽频率的范围越窄，即频率的分辨率越高**

  如果一味的追求频率分辨率，时域区间过短导致，信号输入不完整。如果窗的长度过长，频率分辨率太低会损失很多的频率的细节信息

+ 窗函数的选取

  矩形窗与汉明窗

  ![E6255259CF721AE2007EA92C598CB830](/Users/mac/Desktop/E6255259CF721AE2007EA92C598CB830.JPG)

  过零点：矩形窗的过零点较小，汉明和汉宁窗的过零点较大，越小的过零点意味着主频信息越高，能量越高，损失越低

  旁瓣：矩形窗的衰减更慢，旁瓣对主瓣的影响更高

  为减少旁瓣的影响一般不选取矩形窗

  ![image-20191119145312567](/Users/mac/Library/Application Support/typora-user-images/image-20191119145312567.png)

  ![image-20191119145342178](/Users/mac/Library/Application Support/typora-user-images/image-20191119145342178.png)

  矩形窗中，旁瓣的叠加出现了类似噪声的波形，可能会将一些能量较低的频率信息淹没

  因此一般不采用矩形窗

  ###Sampling and Reconstruction

  ![image-20191119150532711](/Users/mac/Library/Application Support/typora-user-images/image-20191119150532711.png)

  采样对原始信号的频谱进行周期延拓，重建相当于频域乘上低通滤波器，再加上一些增益

  ![image-20191119151541691](/Users/mac/Library/Application Support/typora-user-images/image-20191119151541691.png)

  ### Down-sampling and Up-sampling 

  * Down-sampling

    下采样，通过增加采样周期来降低采样率以及信号的比特率

    <center> Xd(n) = X(nL)</center>

    ![image-20191119152538813](/Users/mac/Library/Application Support/typora-user-images/image-20191119152538813.png)

    因为Xd以2pi为周期，数字角频率w的最大值，在w/L =pi 处取得，为保证不发生混叠，使L>1或者

     ![image-20191119154931300](/Users/mac/Library/Application Support/typora-user-images/image-20191119154931300.png)  

    ![image-20191119155017864](/Users/mac/Library/Application Support/typora-user-images/image-20191119155017864.png)

    ​       时间压缩，频率扩展

  + Up-Sampling 

    ![image-20191119165604508](/Users/mac/Library/Application Support/typora-user-images/image-20191119165604508.png)

    上采样通过补零插值，降低采样间隔，实现采样率的提升

    ![image-20191119165921755](/Users/mac/Library/Application Support/typora-user-images/image-20191119165921755.png)

    ![](/Users/mac/Library/Application Support/typora-user-images/image-20191119170039071.png)

    在频域中表现为，频域间隔的压缩

    ### Quadrature Mirror Filter Bank

    人耳的听觉系统可以当做是由多个不同中心频率的带通滤波器构成，为对某一频率的信号进行处理

    需要将原始信号进行频带划分，一般频带划分会出现混叠的现象

    ![image-20191119171328107](/Users/mac/Library/Application Support/typora-user-images/image-20191119171328107.png)

    为减少，避免混叠现象我们采用在QMF域中进行滤波，其框架大致如下：滤波，下采样，上采样，滤波

    ![image-20191119171440957](/Users/mac/Library/Application Support/typora-user-images/image-20191119171440957.png)

  

  

  

