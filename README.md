# jvmTest

--JVM运行时数据区--
    描述的是java代码在运行时的状态；
    代码只有运行才有价值。
    五个部分
    数据： 方法区 Heap
    指令： 程序计数器、虚拟机栈、本地方法栈

java代码三种代码
    数据、指令、控制
    底层就是这个
    数据流、指令流、控制流
    -------
    程序计数器
        指向当前线程正在执行的字节码指令的地址或行号。
        为什么要记录这个当前正在执行的呢？
            因为CPU 抢占式分片执行、线程存在各种状态
    虚拟机栈
        存储当前线程运行方法时所需要的数据、指令、返回地址。
        先进后出
        进出的最小单位——栈帧
            栈帧最少有四部分：局部变量表、操作数栈、动态链接、出口
        一个栈帧对应一个方法
            局部变量表：局部变量 定长(宽)大小区块，32位
                       8大基本类型 或 引用变量
            操作数栈：又是一个栈，存储数据的地方
        ---反编译指令--
            javap -c -v  文件名.class > p.txt
            这个地方自己看，局部变量表和汇编指令的对应
            动态链接：常量池引用
                     运行时多态，方法执行时才需要去解析。
                     一个接口，有多个实现类。
                     真正执行方法时，需要找到真正的实例，
                     需要到常量池中解析，是在运行时解析。
                     因为常量池里定义了这些多态信息。
                     常量叫做，字面量、符号引用、各种类信息
                    -----常量池需要详细研究下------
            出口：可理解为返回地址。正常、异常
