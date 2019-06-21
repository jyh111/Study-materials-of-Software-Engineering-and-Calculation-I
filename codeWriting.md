codeWriting
============
网络与线程
----------
#### 内容来源于HeadFirst Java P471-P522


### 使用BufferedReader从Socket读取数据


```Java
//别忘了引入包
import java.io.*;(输入、输出）
import java.net.*;(Socket)

//建立Socket连接
Socket chatSocket = new Socket("127.0.0.1",5000); //Socket的两个参数分别代表服务器的IP地址和TCP的端口号,127.0.0.1代表本机

InputStreamReader stream = new InputStreamReader(chatSocket.getInputStream()); //获取来自服务器的信息,即输入流

//建立BufferedReader来读取缓存
BufferedReader reader = new BufferedReader(stream);
String message = reader.readLine();//读取一行
```
<br>

### 用PrintWriter写数据到Socket上
```Java
//引入包
import java.io.*;
import java.net.*;

//建立Socket连接
Socket chatSocket = new Socket("127.0.0.1",5000);

//建立连接到Socket输出流的PrintWriter
PrintWriter writer = new PrintWriter(chatSocket.getOutputStream());

//写入数据
writer.println("message to send");
writer.print("another message"); //注意println 和 print 的区别,前面有换行,后面没有
```

### 编写简单的服务器程序
```Java
//引入包
import java.io.*;
import java.net.*;

//服务器应用程序对特定端口创建出ServerSocket
ServerSocket serverSock = new ServerSocket(4242);

//客户端对服务器应用程序建立Socket连接
Socket socket = new Socket("127.0.0.1",4242);

//服务器创建出与客户端通信的新Socket
Socket socket = serverSock.accept();
```

### 启动新的线程
```Java
//建立Runnable对象(线程的任务)
Runnable threadJob = new MyRunnable();

//建立Thread对象(执行工人)并赋值Runnable(任务)
Thread myThread = new Thread(threadJob);

//启用Thread
myThread.start();
```
