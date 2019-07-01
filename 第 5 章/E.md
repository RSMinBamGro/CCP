2.简要说明 CPU 和 I/O 设备之间传递信息可采用哪几种联络方式，它们分别用于什么场合。<br/>
&emsp;① 立即响应方式<br/>
&emsp;&emsp;&emsp;适用于工作速度十分缓慢的 I/O 设备。<br/>
&emsp;&emsp;&emsp;通常，它们与 CPU 发生联系时已经使其处于某种等待状态，只要 CPU 发出的 I/O 指令到达，它们可以即刻相应。<br/><br/>

&emsp;② 异步工作采用应答信号联络<br/>
&emsp;&emsp;&emsp;适用于工作速度与主机不匹配的 I/O 设备。<br/>
&emsp;&emsp;&emsp;CPU 与 I/O 设备之间存在 I/O 接口，用以暂存数据。I/O 设备与接口之间通过 “Ready” 信号和 “Strobe” 信号表示 CPU 与 I/O 设备间数据的交互。<br/>
![应答信号联络方式](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E5%BC%82%E6%AD%A5%E5%B9%B6%E8%A1%8C%E5%BA%94%E7%AD%94%E8%81%94%E7%BB%9C%E6%96%B9%E5%BC%8F.png)<br/><br/>

&emsp;③ 同步工作采用同步时标联络<br/>
&emsp;&emsp;&emsp;适用于工作速度与 CPU 完全同步的 I/O 设备。<br/>
&emsp;&emsp;&emsp;外部数据若以 2400bqs 的速率传至接口，则 CPU 也必须以 1/24000 的速率接收每一位数。<br/>
<br/><br/>


3.I/O 设备与主机交换信息时共有哪几种控制方式？简述它们的特点。<br/>

&emsp;① 程序查询方式<br/>
&emsp;&emsp;&emsp;CPU 通过程序不断查询 I/O 设备是否已处于准备状态，从而控制 I/O 设备与主机交换信息。<br/>
&emsp;&emsp;&emsp;因为 CPU 需反复查询 I/O 设备状态，存在 “踏步” 现象。<br/>
![程序查询方式流程图](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E7%A8%8B%E5%BA%8F%E6%9F%A5%E8%AF%A2%E6%96%B9%E5%BC%8F.png)<br/>

&emsp;② 程序中断方式<br/>
&emsp;&emsp;&emsp;CPU 启动 I/O 设备后继续执行现行程序，当 I/O 设备准备就绪并向 CPU 发出中断请求后才予以响应。软件方面必须编制中断服务程序。<br/>
&emsp;&emsp;&emsp;CPU 工作效率较程序查询方式更高，不存在 “踏步” 现象。<br/>
![程序中断方式流程图](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E7%A8%8B%E5%BA%8F%E4%B8%AD%E6%96%AD%E6%96%B9%E5%BC%8F.png)<br/>

&emsp;③ DMA 方式<br/>
&emsp;&emsp;&emsp;I/O 设备与主存间存在一条数据通路，能与主存直接交换信息而不占用 CPU 。<br/>
&emsp;&emsp;&emsp;若 DMA 与 CPU 同时访问主存，CPU 总是将总线占有权让给 DMA，称之为窃取。窃取时间一般为一个存取周期。<br/>
![三种方式 CPU 工作效率比较](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E4%B8%89%E7%A7%8D%E6%96%B9%E5%BC%8F%20CPU%20%E5%B7%A5%E4%BD%9C%E6%95%88%E7%8E%87%E6%AF%94%E8%BE%83.png)


11.简述 I/O 接口的功能和基本组成。


12.结合程序查询电路的工作过程，说明其工作原理。


13.说明中断向量地址和入口地址的区别和联系。


16.在什么条件和什么时间，CPU 可以相应 I/O 的中断请求？


18.试以键盘设备为例，结合中断接口电路，说明其工作过程。


19.在程序中断方式中，磁盘申请中断的优先级高于打印机。当打印机正在进行打印时，磁盘申请中断请求。试问是否要将打印机输出停下来，等待磁盘操作结束后，打印机输出才能拿继续进行，为什么？


28.CPU 对 DMA 请求和中断请求的相应时间是否相同？为什么？


29.结合 DMA 接口电路说明其工作过程。


30.在 DMA 的工作方式中，CPU 暂停方式和周期挪用方式的数据传送流程有何不同？画图说明。
