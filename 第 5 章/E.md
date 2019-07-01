2.简要说明 CPU 和 I/O 设备之间传递信息可采用哪几种联络方式，它们分别用于什么场合。<br/>

&emsp;① 立即响应方式<br/>
&emsp;&emsp;&emsp;适用于工作速度十分缓慢的 I/O 设备。<br/>
&emsp;&emsp;&emsp;通常，它们与 CPU 发生联系时已经使其处于某种等待状态，只要 CPU 发出的 I/O 指令到达，它们可以即刻相应。<br/><br/>

&emsp;② 异步工作采用应答信号联络<br/>
&emsp;&emsp;&emsp;适用于工作速度与主机不匹配的 I/O 设备。<br/>
&emsp;&emsp;&emsp;CPU 与 I/O 设备之间存在 I/O 接口，用以暂存数据。I/O 设备与接口之间通过 “Ready” 信号和 “Strobe” 信号表示 CPU 与 I/O 设备间数据的交互。<br/>
![应答信号联络方式](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E5%BC%82%E6%AD%A5%E5%B9%B6%E8%A1%8C%E5%BA%94%E7%AD%94%E8%81%94%E7%BB%9C%E6%96%B9%E5%BC%8F.png)<br/>
<br/><br/>

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
![中断](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E4%B8%AD%E6%96%AD.png)<br/>
&emsp;&emsp;&emsp;CPU 启动 I/O 设备后继续执行现行程序，当 I/O 设备准备就绪并向 CPU 发出中断请求后才予以响应。软件方面必须编制中断服务程序。<br/>
&emsp;&emsp;&emsp;CPU 工作效率较程序查询方式更高，不存在 “踏步” 现象。<br/>
![程序中断方式流程图](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E7%A8%8B%E5%BA%8F%E4%B8%AD%E6%96%AD%E6%96%B9%E5%BC%8F.png)<br/>

&emsp;③ DMA 方式<br/>
&emsp;&emsp;&emsp;I/O 设备与主存间存在一条数据通路，能与主存直接交换信息而不占用 CPU 。<br/>
&emsp;&emsp;&emsp;若 DMA 与 CPU 同时访问主存，CPU 总是将总线占有权让给 DMA，称之为窃取。窃取时间一般为一个存取周期。<br/>
![三种方式 CPU 工作效率比较](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E4%B8%89%E7%A7%8D%E6%96%B9%E5%BC%8F%20CPU%20%E5%B7%A5%E4%BD%9C%E6%95%88%E7%8E%87%E6%AF%94%E8%BE%83.png)<br/>
<br/><br/>


11.简述 I/O 接口的功能和基本组成。<br/>

![I/O 总线与接口部件](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/IO%20%E6%80%BB%E7%BA%BF%E5%92%8C%E6%8E%A5%E5%8F%A3%E9%83%A8%E4%BB%B6.png)<br/>
&emsp;① 选址<br/>
&emsp;&emsp;&emsp;设备选择线上的设备码确定 CPU 选择哪台设备。<br/>
&emsp;&emsp;&emsp;每个接口具有选址功能，当设备码与被设备吗相符时，发出设备选中信号 SEL（通过设备选择电路实现），控制该设备通过，命令线、状态线和数据线与主机交换信息。<br/>

&emsp;② 传送命令<br/>
&emsp;&emsp;&emsp;I/O 设备中设有存放命令的命令寄存器和命令译码器。<br/>
&emsp;&emsp;&emsp;命令寄存器用以存放 I/O 指令中的命令码，受设备选中信号控制。命令线和所有接口电路的命令寄存器相连，只有 SEL 信号有效，命令寄存器才可以接受命令线上的命令码。<br/>

&emsp;③ 传送数据<br/>
&emsp;&emsp;&emsp;接口具有用以完成数据传送的数据通路。<br/>
&emsp;&emsp;&emsp;这种数据通路具有缓冲功能，以将数据暂存在接口内。其实现是通过在接口中设置数据缓冲寄存器，与 I/O 总线中的数据线直接相连。<br/>

&emsp;④ 反应工作状态<br/>
&emsp;&emsp;&emsp;接口中设有能反应设备工作状态的触发器，以便 CPU 及时了解 I/O 设备工作状态。<br/>
![I/O 接口基本组成](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/IO%20%E6%8E%A5%E5%8F%A3%E5%9F%BA%E6%9C%AC%E7%BB%84%E6%88%90.png)<br/>
<br/><br/>


12.结合程序查询电路的工作过程，说明其工作原理。<br/>

![程序查询方式流程](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E7%A8%8B%E5%BA%8F%E6%9F%A5%E8%AF%A2%E6%96%B9%E5%BC%8F%E6%B5%81%E7%A8%8B.png)<br/>
&emsp;① CPU 通过 I/O 指令启动输入设备，指令的设备码字段通过地址线送至设备选择电路。<br/>
&emsp;② 若该接口的设备码与地址线上的代码吻合，其输出 SEL 信号有效。<br/>
&emsp;③ I/O 指令的启动命令经过与非门将工作触发器 B 置 “1”，完成触发器 D 置 “0” ，表示设备处于准备状态。<br/>
&emsp;④ 由 B 触发器启动设备工作。<br/>
&emsp;⑤ 输入设备将数据送至数据缓冲寄存器。<br/>
&emsp;⑥ 由设备发出设备工作结束信号，将 D 置 “1”，B 置 “0”，表示外设准备就绪。<br/>
&emsp;⑦ D 触发器以 “准备就绪” 状态通知 CPU ，表示 “数据缓冲已满” 。<br/>
&emsp;⑧ CPU 执行输入指令，将数据缓冲寄存器中的数据送至 CPU 中的通用寄存器，再存入主存相关单元。<br/>
![程序查询方式接口电路的基本组成](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E7%A8%8B%E5%BA%8F%E6%9F%A5%E8%AF%A2%E6%96%B9%E5%BC%8F%E6%8E%A5%E5%8F%A3%E7%94%B5%E8%B7%AF%E5%9F%BA%E6%9C%AC%E7%BB%84%E6%88%90.png)<br/>
<br/><br/>


13.说明中断向量地址和入口地址的区别和联系。




16.在什么条件和什么时间，CPU 可以相应 I/O 的中断请求？


18.试以键盘设备为例，结合中断接口电路，说明其工作过程。


19.在程序中断方式中，磁盘申请中断的优先级高于打印机。当打印机正在进行打印时，磁盘申请中断请求。试问是否要将打印机输出停下来，等待磁盘操作结束后，打印机输出才能拿继续进行，为什么？


28.CPU 对 DMA 请求和中断请求的相应时间是否相同？为什么？


29.结合 DMA 接口电路说明其工作过程。


30.在 DMA 的工作方式中，CPU 暂停方式和周期挪用方式的数据传送流程有何不同？画图说明。
