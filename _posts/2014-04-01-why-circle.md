---
layout: post
title: 为什么是圆？
abstract: 相同周长的封闭曲线，为什么圆围成的面积最大？
---

最近看普林斯顿分析系列的一本傅里叶分析，看得很爽。但凡写数学书的人，往往为了严密，要把自己的思想琢磨来琢磨去，很容易把原先灵光一闪的部分磨到面目全非。常常看到各种证明，突如其来的构造出一个式子，一时间奇妙尽现眼底，但是你永远也不知道作者是怎么想到这个构造的。所以我喜欢的数学书，最好能展示出来作者的思路，当前有什么，我们要什么，往哪个方向走，如能传达出一步一步背后的动机，就比较容易给人以启示。相比之下数学的严密性却不那么重要。有了思路，再慢慢完善，更符合一般人解决问题的本质。

今天刚好看到一个很有意思的命题：相同周长的封闭曲线，圆围成的面积最大。这大概是常识吧，很久以前就知道了，而且相当直观。从吹泡泡的经验看，不仅二维如此，三维也是如此。一个胡诌的解释就是，既然要取最值，那么此时曲线的状态必然十分特殊，这样特殊的状态肯定比较少。如果图形不对称的话，镜像或者旋转都会得到一个面积相同但是图形不同的状态，这就不满足'特殊'这个要求。往往极值和对称都有着不解之缘，函数取到极值那个地方，截取一小撮的话也是比较'对称'的。而圆是最对称的了。

言归正传，严格的证明似乎毫无头绪。周长要怎么和面积联系起来呢，一个是线积分，一个是面积分，自然想到了格林公式。

格林公式

这也对曲线如何建模提供了思路。既然要用格林公式，左边是线积分，那最好就是表示成'运动'参数形式了：( x(t), y(t) )，t属于(0, T)，t从0变到T，就等于曲线上一个小人沿着曲线跑一圈，因此( x(0), y(0) )==( x(T), y(T) )，换言之x，y都是t的周期函数，周期为T。这是封闭的条件，同时又为勾搭上傅里叶级数创造了条件。然后再加三个限制：

为了方便计算，可以把T取成2pi。反正我们只关心曲线，对于这个小人跑一圈要费多少时间是无所谓的。 这样一来，计算周长就成了sqrt(x'2+y'2)对t积分。为了方便计算，我们让这个小人速度恒定。v=sqrt(x'2+y'2)不变。如此一来，周长就变成了2piv。pi表示圆周率。曲线为圆的情况下，半径就是v，面积就是piv2，证明圆面积最大，就是要证明一般曲线面积S<=piv2。 另外我们还希望他不要乱跑，要符合物理规律，不要这一刻还停在一边喘气，下一刻又撒腿飞奔。总之我们可以保证加速度存在。这样x, y就二阶可导。可以保证傅里叶级数收敛于原函数。 上面的格林公式如果把右边括号内弄成1，就是面积了。最简单的办法就是令B等于x，A等于0。这样就有了：

B=x,A=0

由于x,y都是2pi周期的函数，傅里叶展开就得到：

傅立叶展开

现在x和y'做乘法，相当于x的每一项和y'的每一项相乘，很可怕。但是外面还有个积分。在x的傅里叶级数中随便取一项aneint，它要和y'每一项相乘，但是除非y'那边拿出的是b-ni(-n)e-int，其他的积分出来都是0。这就是eint的正交性。

eint * eimt = ei(n+m)t，除非m+n等于0，此时式子等于1，从0积分到2pi就是2pi。否则这个式子t从0取到2pi，就是绕着单位圆转m+n圈，积分结果就是0。 这样使得对x每一项，y'那边也只有一项有效，并且这两项的下标对称。这样乘出来不仅结果只有一个求和号，而且积分也可以一并算了。由于x，y都是二阶可导的（这是个充分不必要条件），傅里叶级数收敛于原函数，把那个蚯蚓符号换成等号，于是乎：

傅立叶级数乘法

最后一个等号是因为上式是个实数，所以它的共轭等于它本身，把an,bn都取共轭，再把i改成-i，就是整个的共轭了。并且b-n的共轭就等于bn：

对称下标互为共轭 第一个等号是因为y是实函数，虚数部分为0，所以取共轭不变。第二个等号是把i换成-i，bn取共轭，最后一个等号是变换循环变量，把n换成-n。然后两端对比系数就知道bn与b-n互为共轭。

这是面积那一边，再看周长那一边。

image

从第二个等号就可以看出令速度恒定的好处，因为积分式里再来个根号是很不好处理的。第三个等号就是x'，y'分别写成傅里叶级数再平方，和上面做乘法一样，其中又用到eint的正交性。另一个更直观的解释就是，傅里叶展开等同于基的变换，eint是一组标准正交基。其中内积的定义是在周期上积分再除周期。那样的话eint前面的系数其实就是在新的基下的坐标。在标准正交基下，向量的模长就等于坐标的'模长'。化为标准正交基，这也是傅里叶级数的动机。

整理一下前面的式子。前面的S是有正负的（和曲线积分方向有关），这里我们只关心大小，取绝对值：

面积和速度

这是我们现在手头有的，想要的是S<=piv2，看上去已经有点雏形了吧。原书其实没有引入v，而是进一步把速度限为1，方便了一些计算，但是也少了一些信息。因为1平方虽然还是1，但其实单位是不一样的。分析学有着深刻的物理背景，我认为对每个式子最好都要把单位搞清楚。上面两式右边的'单位'都是系数模长的平方，说明左边'单位'也是一样的，才有比较的可能。正好我们想要证明的也是S和v2比较。做到这一步看见式子中出现v2，就比单单一个1让人觉得放心不少。

接下来用不等式两个不等式，a,b是两个复数，绝对值号表示模长。第一个不等号可以看成是两个二维向量的内积，好像叫余弦定理吧，仅当向量同向取等。第二个不等式当且仅当a,b模长一样时取等。于是有：

逐步放大面积S

首先是把模长符号放到求和以内，这样会放大，除非每一项都同向。然后用上面的不等式，另外有|n|<=n2，当且仅n为-1,0,1取等。

现在再看取等得情况。就从n的缩放入手，取等的话n只能为-1,0,1，就是说其他项全是0。看上式第二行左边n缩放的那一步，|n|右边所乘的因子已经是平方和了，要想为0，就是an，bn都为0。于是x和y中，也只有n等于-1,0,1这几项了：

仅三项的傅立叶级数

利用欧拉公式，可以化为：

欧拉公式化为正弦余弦

大致已可见端倪，可以看出x方向的运动已经是一个以a0为中心，2|a1|为振幅的简谐振动。y同理。再看前面的不等式何时取等，一个是an.bn模相等，一个是an和-bni要同向，就是(Re(a1), Im(a1))与(Im(b1),-Re(b1))同向且同模，所以Re(a1)==Im(b1),Im(a1)==-Re(b1)。这时也可以验证anbn共轭in中每一项都是实数。所以第一个不等号也取等。取Re(a),Im(a)为A/2，-B/2，最后就得：

圆的参数方程

这就是圆了。

另外原书还有一个条件是simple，就是说曲线不交叉，按照上面面积的算法，曲线总是有方向，总是取沿曲线方向的左边为正，那对于交叉的封闭曲线，比如一个8字型，如果取下面那个圆逆时针，面积就是下面的圆减去上面的圆。这样算出来总面积可正可负，再取绝对值为总面积。直觉告诉我们这种交叉的曲线面积不可能最大。但是这样算出来的面积对交叉的曲线确实有失公平。因此还是加上这个条件。

参考书目：

Elias M. Stein, Rami Shakarchi "Fourier Analysis An Introduction"