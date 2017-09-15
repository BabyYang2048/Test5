# Test5  ---使用Handler处理消息
    使用Handler在新线程中发送消息，然后在主线程中处理消息
      1.了解ANR，理解线程编程。
      2.学会使用Handler处理消息。
      3.编程实现在新线程中发送消息，然后在主线程中处理消息。
      
       
       ----创建一个handle对象，用匿名类写内部方法，注意要有重写
       final Handler handler = new Handler(){
          @Override
            public  void  handleMessage(Message msg) {
                textView.setText(msg.arg1+"");
          }
        };

        ----创建Runnable接口并重写run方法
        final Runnable myWorker = new Runnable() {
            @Override
            public void run() {
               //功能代码...
            }
        };

        ----创建新线程并实现Runnable对象
          Thread workThread = new Thread(null,myWorker,"WorkThread");
                
        ----启动线程        
          workThread.start();
          
        在run方法中
               用Hander.sendMessage(Message)将消息发送给主线程
               在主线程Handler.handleMessage()中接收并处理该消息
        
        注意有一点：
        Android不能再子线程中直接修改UI界面，只可以通过handler在主线程中处理。
        
