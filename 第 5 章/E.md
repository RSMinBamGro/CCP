2.简要说明 CPU 和 I/O 设备之间传递信息可采用哪几种联络方式，它们分别用于什么场合。<br/>
&emsp;① 立即响应方式<br/>
&emsp;&emsp;&emsp;适用于工作速度十分缓慢的 I/O 设备。<br/>
&emsp;&emsp;&emsp;通常，它们与 CPU 发生联系时已经使其处于某种等待状态，只要 CPU 发出的 I/O 指令到达，它们可以即刻相应。<br/>
&emsp;② 异步工作采用应答信号联络<br/>
&emsp;&emsp;&emsp;适用于工作速度与主机不匹配的 I/O 设备。<br/>
&emsp;&emsp;&emsp;CPU 与 I/O 设备之间存在 I/O 接口，用以暂存数据。I/O 设备与接口之间通过 “Ready” 信号和 “Strobe” 信号表示 CPU 与 I/O 设备间数据的交互。<br/>
![应答信号联络方式](https://github.com/RSMinBamGro/CCP-Exercises/blob/master/%E7%AC%AC%205%20%E7%AB%A0/%E5%BC%82%E6%AD%A5%E5%B9%B6%E8%A1%8C%E5%BA%94%E7%AD%94%E8%81%94%E7%BB%9C%E6%96%B9%E5%BC%8F.png)<br/>
&emsp;③ 同步工作采用同步时标联络<br/>
&emsp;&emsp;&emsp;适用于工作速度与 CPU 完全同步的 I/O 设备。<br/>
&emsp;&emsp;&emsp;外部数据若以 2400bqs 的速率传至接口，则 CPU 也必须以 1/24000 的速率接收每一位数。<br/>
<br/><br/>
