android性能优化一般包括以下几点：
- 资源优化
- 布局优化
- 绘制优化
- 内存泄漏优化
- 无响应优化
- 线程优化

#### 资源优化

资源优化一般指的是图片资源，就是图片资源尽量压缩，这样加载的时候消耗内存就会变小。

#### 布局优化

布局优化的思想就是减少层级，如果同时能用 LinearLayout 和 RelativeLayout 的情况下，用 LinearLayout，因为 RelativeLayout 比较复杂，
会花费更多CPU时间，FrameLayout 和 LinearLayout 一样都是一种简单高效的 ViewGroup。  
还有使用各种标签：
- <include>：将一个指定的布局文件加载到当前的布局文件中，只支持 android:layout_ 开头的属性，id 除外。
- <merge>：减少布局层级。
- ViewStub：继承了 View，宽高为0，不参与任何布局的绘制过程，意义在于按需加载布局文件。

#### 绘制优化

绘制优化是指在 onDraw 里面避免大量的操作。
- 在 onDraw 里面不要创建新的局部对象，因为 onDraw 方法可能会被频繁的调用。
- onDraw 不要做耗时的任务，也不能执行成千上万次的循环。

#### 内存泄漏优化

- 静态变量导致的内存泄漏
- 单例模式导致的内存泄漏，单例模式的特点是它的生命周期是与 Application 保持一致，如果在单例模式中使用的资源没有及时地释放就会被使用者持有，
不能释放，比如在单例模式中注册了一个监听器，但是在界面销毁的时候没有进行解注册操作。
- 动画导致的内存泄漏，在界面销毁的时候要去停止和释放动画资源。

#### 无响应优化

核心思想是不要在主线程做耗时操作。将耗时操作放到线程中执行，采用异步的方式执行耗时操作。  

#### 线程优化

线程优化就是要使用线程池，线程池可以重用内部的线程，从而避免了线程的创建和销毁所带来的开销

#### 优化建议

- 避免创建过多的对象
- 不要使用枚举，枚举占用的内存空间比整形大
- 常量尽量使用 static final 来修饰
- 使用一些 android 特有的数据结构，比如 SparseArray 和 Pair 等，他们都有更好的性能
- 适当的使用软应用和弱应用
- 采用内存缓存和磁盘缓存
- 尽量使用静态内部类，可以避免潜在的由于内部类而导致的内存泄漏




