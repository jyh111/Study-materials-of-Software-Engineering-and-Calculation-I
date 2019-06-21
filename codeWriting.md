codeWriting
============
网络与线程
----------
#### 内容来源于HeadFirst Java P471-P522
理解记忆 P518-521 <br>
理解P505-515的故事(线程锁)

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
Socket socket = serverSock.accept();  //accept()方法会停下来,直到等接受到客户端的连接请求才会继续
```

### 启动新的线程
```Java
//建立任务
public class MyRunnable implements Runnable{ //Runnable接口

    public void run(){ //需要实现run方法,即线程需要做的任务
        System.out.println("Calm down in whatever condition");
    }
}

//建立Runnable对象(线程的任务)
Runnable threadJob = new MyRunnable();

//建立Thread对象(执行工人)并赋值Runnable(任务)
Thread myThread = new Thread(threadJob);

//启用Thread
myThread.start();
```

### 让线程小睡一下(暂时休眠)
```Java
public class MyRunnable implements Runnable{
    public void run(){
        //让线程小睡一下
        try{
            Thread.sleep(2*1000); //2000毫秒,即两秒
        }catch(InterruptedException ex){
            ex.printStackTrace();
        }
    }
}
```

### 线程锁
```
//保证syncronized的方法会一起执行完毕,中间不会有其它线程插进

public synchronized void increment(){
    //方法实现
}
```

### 理解要点
* 网络部分
  * 客户端与服务器的应用程序通过Socket连接来接通
  * 客户端需要知道服务器的IP地址和端口号
  * 0~1023的端口号是保留给HTTP、FTP、SMTP等已知的服务
  * 服务器可以使用ServerSocket来等待用户对特定端口的请求,当ServerSocket接受到请求时，它会做一个Socket来接来接受客户端请求
* 线程部分
  * 线程和可以实现同时执行的能力,每个线程有独立的任务
  * java虚拟机通过短时间内对线程交替执行实现看起来的同时执行
  * 线程的调用由线程调度器决定,无法控制线程的调用,线程的调用是随机、不可预测的
  * 可以通过使一个线程进入睡眠给其它线程执行的机会
  * 可以通过同步化方法确保一段代码一起执行
  * 同步化可能会发生死锁的情况,即两个同步化方法分别需要进入彼此而停机
