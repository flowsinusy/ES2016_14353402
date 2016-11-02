# LAB THREE
## 实验任务
### Task One
修改example1，使其输出三次方数。<br/>
修改方法：在square.c文件中，将信号处理函数修改为，读入输入端信号i，将其三次方后写到输出端即可，i = i * i * i。<br/>
运行结果截图：<br/>
![example1运行结果][1]<br/>
dot文件截图：<br/>
![example1运行后的dot截图][2]

### Task Two
修改example2，让3个square模块变为2个。<br/>
修改方法：通过迭代，定义2个square，即将迭代的variable的value改为2即可。<br/>
运行结果截图：<br/>
![example2运行结果][3]<br/>
dot文件截图：<br/>
![example2运行后的dot截图][4]

## 实验原理同感想
examples中各文件的含义：<br/>
src文件夹：各个进程，包括生产者、消费者和处理模块等，的功能定义。<br/>
exampleX.xml文件：系统架构即模块连接方式的定义。<br/><br/>

首先看generator.c文件，里面定义了生产者进程。<br/>
1）generator_init是初始化函数，将当前位置置为0，并设置生产者长度。这里的local指针指向的是.h文件中的_local_states结构。<br/>
2）generator_fire是信号产生函数，如果当前位置小于生产长度，则将当前下标写到输出端，否则销毁进程，也就是让这个程序被发射、开火、执行Length次之后停下来。<br/><br/>

然后是consumer.c文件，里面定义了消费者进程。<br/>
1）consumer_init是初始化函数。<br/>
2）consumer_fire是信号消费函数，若当前位置小于设定长度，则读出输入端信号，并且打印，否则销毁进程。<br/><br/>

最后是square.c文件，里面定义了平方进程。<br/>
square_fire是信号处理函数，读入输入端信号i，将其平方后写到输出端，在重复Length次之后停止。<br/><br/>

在xml文件里，process就是框，sw_channel就是线，connection就是把线的那头连到框的那头。<br/><br/>

要运行这些程序，首先进入dol文件夹（cd dol），进入路径（cd build/bin/main)，然后编译并运行文件（sudo ant -f runexample.xml -Dnumber=X），如果是重新编译先在build/bin/main下删除对应的文件夹。在终端可以看到运行结果，打开build/bin/main在对应文件夹下可以看到所运行的example的dot图。<br/> 

  [1]: ./images/one.jpg "one.jpg"
  [2]: ./images/oneDot.jpg "oneDot.jpg"
  [3]: ./images/two.jpg "two.jpg"
  [4]: ./images/twoDot.jpg "twoDot.jpg"
