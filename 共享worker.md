## 共享worker ##

即一个worker被多个脚本使用，即使这些脚本正在被不同的window、iframe或者worker访问。

> 共享worker也受同源策略限制，即被访问的浏览上下文必须属于同源。

### 生成共享worker ###

	var myWorker = new SharedWorker('worker.js');

与专用worker的一个最大区别是，共享worker必须通过一个确切打开的端口供脚本和worker通信（在专用worker中这一部分是隐式进行的）。

在传递消息前，端口连接必须被显式的打开，打开方式是使用onmessage事件处理函数或者sart()方法。start方法的调用只在消息事件被addEventListener方法使用。

在使用start方法的打开端口连接，如果父级线程和worker线程需要双向通信，就都需要调用start方法。

	myWorker.port.start(); //表示父级线程的调用
	port.start();	// worker线程中的调用

### 消息的接收和发送 ###

同专用worker一样，但是postMessage()方法必须被端口对象调用。

在一个端口连接被创建时，worker中使用onconnect事件处理函数来执行代码。

### 数据的接受和发送 ###

主页面和worker之间的数据一般是拷贝传递，而且传递对象都是需要经过序列化，在另一端反序列化。





