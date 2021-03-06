# -offer_algorithm

# SQL事务

## 把多条语句作为整体进行操作的功能成为数据库事务

SQL数据库事务的四个特性ACID：

A：Atomic原子性，是指将所有SQL作为原子单元执行，要么全部执行，要么全部不执行

C: Consistent一致性，即完成事务后，所有数据的状态都是一致的，如果A减去了100，则B一定加上了100

I: Isolation隔离性，如果多个事务并发执行，则每个事务作出的修改必须与其他事务进行隔离。

D: Duration持久性，即事务完成后，对数据库数据的修改会被持久化存储。

# StringBuilder

由于String在进行拼接时会产生新的字符串，为了避免费时和费空间，引入了StringBuilder，可以随时添加新的子串，并在合适的时候toString()转化为字符串。

<Strong> 前身是StringBuffer,它的效率低，但是允许多线程执行添加或删除。如果所有字符串都在单线程中编辑，则直接使用StringBuilder.

# Arrays
  
Arrays.sort(type[] a)采用了快速排序算法，效率比较高。 <stong>必须实现了Comparable接口中的compareTo方法。
  
Arrays.copyOf(type[] a,int length)返回复制的新数组，Arrays.copyOfRange(type[] a,int start,innt end)，start和end均表示下表，end不包含。即copy后的长度为end-start.
  
Arrays.binarySearch(type[] a,int start,int end,type v)二分法查找值v，如果找到返回下标，未找到则返回负值r，并且-r-1是当保持a有序时，v应该插入的位置。
  
Arrays.fill(type [],type v)将所有数据元素的值设置未v。
  
  Arrays.equals(type[] a,type[] b)比较两数组大小和对应元素是否都相等，返回bool。
  
  # Http流程
  
  ## 浏览器端发出HTTP请求
  
  1.构建请求，例如get
  
  2.查找缓存，如果查找成功则拦截请求，否则接着发送网络请求。
  
  3.通过解析URL来获取服务器IP和端口，并建立TCP连接
  
  4.此时如果TCP队列满了，就等待，否则直接建立连接
  
  5.通过3次握手建立确认连接，至此正式实现服务器与客户端的连接。
  
  6.发送http请求，首先是请求行（请求方法，URL，HTTP版本协议），然后发送附加的信息请求头（浏览器所使用的操作系统以及浏览器内核等）和请求体
  
  ## 服务器处理HTTP请求
  
  1. 返回请求（响应行，包含状态码和协议版本，如果响应码为200，则服务器处理成功），响应头（服务器自身信息，返回时间以及数据类型（json等）），响应体（包含了实际请求的内容)
  
  2. 断开连接，四次挥手
  
  ## 三次握手
  
  刚开始客户端处于 closed 的状态，服务端处于 listen 状态。然后
  
1、第一次握手：客户端给服务端发一个 SYN 报文，并指明客户端的初始化序列号 SN(c)。此时客户端处于 SYN_Send 状态。
  
2、第二次握手：服务器收到客户端的 SYN 报文之后，会以自己的 SYN 报文作为应答，并且也是指定了自己的初始化序列号 ISN(s)，同时会把客户端的 ISN + 1 作为 ACK 的值，表示自己已经收到了客户端的 SYN，此时服务器处于 *SYN_REVD* 的状态。
  
3、第三次握手：客户端收到 SYN 报文之后，会发送一个 ACK 报文，当然，也是一样把服务器的 ISN + 1 作为 ACK 的值，表示已经收到了服务端的 SYN 报文，此时客户端处于 establised 状态。
  
4、服务器收到 ACK 报文之后，也处于 establised 状态，此时，双方以建立起了链接。
  
  ## 四次挥手
  
  1、第一次挥手：客户端发送一个 FIN 报文，报文中会指定一个序列号。此时客户端处于FIN_WAIT1状态。
  
2、第二次握手：服务端收到 FIN 之后，会发送 ACK 报文，且把客户端的序列号值 + 1 作为 ACK 报文的序列号值，表明已经收到客户端的报文了，此时服务端处于 CLOSE_WAIT状态。
  
3、第三次挥手：如果服务端也想断开连接了，和客户端的第一次挥手一样，发给 FIN 报文，且指定一个序列号。此时服务端处于 LAST_ACK 的状态。
  
4、第四次挥手：客户端收到 FIN 之后，一样发送一个 ACK 报文作为应答，且把服务端的序列号值 + 1 作为自己 ACK 报文的序列号值，此时客户端处于 TIME_WAIT 状态。需要过一阵子以确保服务端收到自己的 ACK 报文之后才会进入 CLOSED 状态
  
5、服务端收到 ACK 报文之后，就处于关闭连接了，处于 CLOSED 状态。
  
  ## 多态的体现
  
  1.对象变量，既可以是a，也可以是a的子对象。
  
  ## 哈希码
  
  存放对象的存储地址。 如果重新定义equals方法，则必须重新定义哈希码方法，以便用户将对象插入hash表中。并且equals和hash码的定义必须一致，如果equals放回true，那么hashcode必须有相同的值
  
  ## 线程和进程的区别
  
  进程是应用程序一次执行的过程，是程序在执行过程中进行分配和调度资源的基本单位，每个进程有自己的地址空间，每启动一个进程，系统就会为它分配地址空间，建立数据表来维护代码段、堆栈段和数据段，开销很大
  
  线程是CPU执行资源调度的最小单位，共享进程中的数据，使用相同的地址空间，因此切换以及创建线程的开销小很多
  
  线程是进程的执行单元，一个程序至少有一个进程，一个进程至少有一个线程。
  
  地址空间区别：同一进程的线程共享本进程的地址空间，而进程之间则是独立的地址空间
  
  资源区别：同一进程的线程会共享本进程的资源如内存、I/O，cpu等等，但是进程之间资源独立。
  
  一个进程如果崩溃，不会对其他进程造成影响，但是一个线程崩溃会导致整个进程死掉，所以多进程要比多线程健壮。
  
  进程切换时消耗资源大，效率低。涉及频繁切换时线程好于进程。如果要求同时进行并且共享某些变量的并发操作，是只能用线程不能用进程的。
  
  执行过程的区别：每个进程都有一个程序运行的入口，但是线程不能独立执行。
  
  ## 异步消息处理机制
  
  1. Message ： 线程间传递的消息，可以内部携带少量信息，用于在不同线程之间交换数据 。
  
  2. Handler ： 用于发送和处理消息。 new Handler().sendMessage() 发送消息（子线程），handlerMessage() 处理消息更新UI（主线程）
  
  3. MesseageQueue ： 消息队列，用于存放所有通过Handler发送的消息，这些消息存放于队列中等待被处理。每个线程只有一个消息队列。
  
  4. Looper ： 线程中消息队列的管家，当调用Looper.loop()后，进入无限循环，当消息队列中存在一条消息时，就取出并传递给handlerMessage()方法。 每个线程只能有一个Looper对象。
  
  过程： 主线程创建Handelr对象，并重写handleMessage()方法。当子线程需要UI操作时，创建Message对象，并通过Handler发送出去，之后这条消息被加入消息队列等待处理，Looper则一直尝试从消息队列中取出消息，最后发回handlerMessage()方法中。
 
  ```
  //MainThread
  
  private Handler handler=new Handler(Looper.getMainLooper){
  
  public void handlerMessage(Message msg){...}
  
  //NewThread
  
  new Thread(new Runnable(){
  
  @Override
  
  public void run(){
  
  Message message=new Message();
  
  message.what  =  1;
  
  handler.sendMessage(message);
  
  }).start();
  
  ```
  
  # AsyncTask
  
  基于异步消息处理机制。 这是一个抽象类，需要继承。
  
  class DownloadTask extends AsyncTask<Void,Integer,Boolean>{...}
  
  ### 三个泛型参数分别代表
  
  执行后台任务需要传递的参数，用于后台任务中使用。
  
  后台任务执行时，如果需要在界面上显示当前进度，作为进度单位。
  
  当任务执行结束后，将结果返回，作为返回值类型。
  
  ### 需要重写：
  
  onPreExecute(): 在后台任务开始前调用，用于在界面上的初始化操作，比如显示一个进度条对话框等。
  
  doInBackground(Params...): 该方法的所有代码都会在子线程中运行，应该在此处完成耗时任务，任务一旦完成则返回运行结果。 如果要反馈一些元素，如反馈当前任务的执行进度，可以调用publishProgress(Progress...)来完成。
  
  onProgressUpdate(Progress...): 当后台任务中使用了publishProgress(progress...),则很快调用这个方法，参数就是后台任务中传递过来的，在这个方法中可以进行UI操作，利用参数中的数值就可以更新界面元素。
  
  onPostExcute(Result): 当后台任务完成并return时，这个方法很快被调用，参数也由后台任务传递过来，在这个方法中可以利用返回的数值进行UI操作，比如说提醒任务执行的结果，以及关掉进度条对话框。
  
## 服务
  
  需要继承Service类，并且必须重写onBind()方法。  必须在AndroidManifest.xml文件中进行注册才能生效，也证明它是四大组件之一。
  
  onCreate() 在服务创建的时候调用
  
  onStartCommand() 在每次启动服务的时候调用
  
  ##### 在第一次创建服务的时候，会调用onCreate()方法和onStartCommand()方法，但如果多次启动服务，就只有onStartCommand()方法得到执行。
  
  onDestroy() 在服务销毁的时候调用
  
  ```
  \\启动服务
  
  Intent intent=new Intent(this, service.class);
  
  startService(intent);
  
  \\结束服务
  
  stopService(intent);
  
  ```
  
  活动与服务之间通过onBind()方法进行通信，创建Binder对象对Service进行管理
  
  ```
  
  \\服务
  
  Public class myService extends Service{
  
    private DownloadBinder mBbinder=new DownloadBinder();
  
    class DownloadBinder extends Binder{
  
      public void startDownload(){...}
  
      public int getProgress(){...}
  
    }
  
    @Override
  
    public IBinder onBind(Intent intent){
  
      return mBinder;
  
    }
  
  }
  
  \\活动
  
  private myService.DownloadBinder binder;
  
  privte ServiceConnection connection=new ServiceConnection(){
  
    @Override
  
    public void onServiceConnected(ComponentName name,IBinder service){
  
      binder=(myService.DownloadBinder)service;
  
      binder.startDownload();
  
      binder.getProgress();
  
    }
  
    @Override
  
    public void onServiceDisconnectd(ComponentName name){}
  
  }
  
  \\开启服务和绑定服务
  
  Intent intent=new Intent(this, myService.class);
  
  \\BIND AUTO CREATE表示绑定后自动创建活动，使myService中的onCreate()方法得到执行，但onStartCommand()不执行。
  
  bindService(intent,connection,BIND AUTO CREATE);
  
  startService(intent);
  
  ```
  
  ## 服务的生命周期
  
  一旦项目的任何位置调用了Context的startService()方法，则服务启动，并且回调onStartCommand()方法，如果服务没有创建过，则会先执行onCreate()方法。服务启动后会一直执行直到调用stopService()或者stopSelf()方法被调用。
  
 ######  <font color="red">注意：虽然onStartCommand()可以执行多次，但是实际上服务只存在一个实例，无论调用多少次startService()方法，只需调用一次stopService()或者stopSelf()方法即可停止。</font>
  
  另外，还可以调用Context的bindService()来获取一个服务的持久连接，这样会回调onBind()方法。如果服务未创建过，则onCreate()先于onBind()方法执行。之后，调用方就可以获取返回的IBinder对象的实例，自由地与服务通信了。只要连接没有断开，就会一直保持运行。
  
  之后调用stopService()或者unBindService()即可停止服务，onDestroy()方法会执行，这样服务就销毁了。如果startService()和bindService()同时执行了的话，必须同时执行stopService和unBindService()。
  
  ## 使用Notification
  
  既可以在活动里创建，也可以在广播接收器里创建，也可以在服务里创建。
  
  首先需要一个NotificationManager对通知进行管理，可以调用Context的getSystemService()得到。
  
  ```
  
  NotificationManager manager=(NotificationManager)getSystemService(Context.NOTIFICATION_SERVICE);
  
  NotificationCompat.Builder builder=new NotificationCampat.Builder(Context);
  
  manager.notify(id,new Notification.build()); //这里的Notification对象即是builder.
  
  ```
  
  在build()方法之前可以连缀任意的设置方法来丰富这个对象。通知设置后，通过notify()函数，即可让通知显示出来。
  
  ### 使通知可点击
  
  利用PendingIntent（延迟执行的Intent, 在某个合适的时机去执行某个动作）
  
  获取实例后，根据需求选择使用getActivity()、getBroadCast()还是getService()方法，参数(Context,0,New Intent,行为常量(FLAG_NO_SHOT等等一般为0))
  
  ```
  
  Intent intent=new Intent(this, Activity.class);
  
  PendingIntent pi=PendingIntent.getActivity(this,0,intent,PendingIntent.FLAG_ONE_SHOT);
  
  .setContentIntent(pi);
  
  ```
  
  ###设置声音
  
  ```
  
    \\设置声音
  
   Uri defaultSoundUri = RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION);
  
  .setSound(defultSoundUri);
  
  ```
  
  # HashTable 
  
  散列表为每个对象计算一个整数，称为散列码（hash code）。散列码是由对象的实例域产生的一个整数。在Java中，散列表用链表数组实现。每个列表被称为桶。要想查找表中对象的位置，就要先计算它的散列码，然后与桶的总数取余，所得到的结果就是保存这个元素的桶的索引。
  
  桶被占满的情况，这也是不可避免的。这种现象被称为散列冲突。 这时，需要用新对象与桶中的所有对象进行比较，查看这个对象是否已经存在。如果散列码是合理且随机分布的，桶的数目也足够大，需要比较的次数就会很少
  
  散列表可以用于实现几个重要的数据结构。其中最简单的是set类型。set是没有重复元素的元素集合。set的add方法首先在集中查找要添加的对象，如果不存在，就将这个对象添加进去。Java集合类库提供了一个HashSet类，它实现了基于散列表的集。可以用add方法添加元素。contains方法已经被重新定义，用来快速地查看是否某个元素已经出现在集中。它只在某个桶中查找元素，而不必查看集合中的所有元素。散列集迭代器将依次访问所有的桶。由于散列将元素分散在表的各个位置上，所以访问它们的顺序几乎是随机的。只有不关心集合中元素的顺序时才应该使用HashSet。
