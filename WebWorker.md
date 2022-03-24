# Web Worker #

Web Worker为js提供了一个多线程解决方案，而不再受限于浏览器一个js主进程的束缚。

## 特点： ##

1. worker对象运行的js仅能被首次生成它的脚本使用。
2. 在worker内，是不能直接操作DOM的，也不能使用`window`对象的默认方法和属性，但是仍可以使用WebSocket，indexedDB。
3. worker和主线程之间通过消息通知机制来实现数据传递，双方都使用postMessage（）方法发送各自的消息，通过onmessage事件处理相应的消息。
4. 只要同源，worker可以依次生成新的worker，并且使用XHR进行网络I/O。

## worker特性检测 ##

    if (window.Worker) {
	...	
	}

## worker生成 ##

	new Worker('xxx.js')

## worker终止 ##

在主线程中终止创建的worker，可以使用`worker.terminate()`
在worker线程中，使用`close()`

## 引入脚本与库 ##

worker线程可以访问一个全局函数`importScripts()`

## 以上说的是常用的专用worker，即只能被创建线程访问的worker，还有一类共享worker ##

//插入 共享 worker的兼容性图