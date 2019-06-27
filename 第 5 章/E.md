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
![程序查询方式流程图]()

&emsp;② 程序中断方式<br/>
&emsp;&emsp;&emsp;CPU 启动 I/O 设备后继续执行现行程序，当 I/O 设备准备就绪并向 CPU 发出中断请求后才予以响应。软件方面必须编制中断服务程序。<br/>
&emsp;&emsp;&emsp;CPU 工作效率较程序查询方式更高，不存在 “踏步” 现象。<br/>
![程序中断方式流程图]()

&emsp;③ DMA 方式<br/>
&emsp;&emsp;&emsp;I/O 设备与主存间存在一条数据通路，能与主存直接交换信息而不占用 CPU 。<br/>
&emsp;&emsp;&emsp;若 DMA 与 CPU 同时访问主存，CPU 总是将总线占有权让给 DMA，称之为窃取。窃取时间一般为一个存取周期。<br/>
