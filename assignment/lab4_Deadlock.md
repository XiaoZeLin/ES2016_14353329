# Lab4： 死锁

_ _ _

##### 概要
嵌入式系统试验lab 4的实验目的是理解死锁概念和分析死锁产生条件。实验主要报告包括三部分：死锁结果截图、产生死锁的四个必要条件和分析样例完之前程序产生死锁的原因。


##### 死锁结果截图
实验代码：

###### 定义三个java类,保存为Deadlock.java文件
```
class A{
	synchronized void methodA(B b){
		b.last();
	}
	
	synchronized void last(){
		System.out.println("Inside A.last()");
	}
};

class B{
	synchronized void methodB(A a){
		a.last();
	}
	
	synchronized void last(){
		System.out.println("Inside B.last()");
	}
};

class Deadlock implements Runnable{	
	A a = new A();
	B b = new B();
	
	Deadlock(){
		Thread t = new Thread(this);
		int count = 20000;
		
		t.start();
		while(count-->0);
		a.methodA(b);
	}
	
	public void run(){
		b.methodB(a);
		
	}
    public static void main(String args[]){
		new Deadlock();
	}
}
```
###### Linux系统运行过程：

```
1. javac Deadlock.java
2. java Deadlock
3. 命令行执行：
   for((c = 1;c<=100;c++))
   do
      echo "$c times"
      java Deadlock
   done
```

实验结果截图如下：

![](https://cloud.githubusercontent.com/assets/22488425/20049955/6df25c96-a501-11e6-848f-6ca8c448b2cc.jpg)

##### 死锁四个必要条件
1. 互斥条件：一个资源每次只能被一个进程使用
2. 请求与保持条件：一个进程因请求资源而阻塞时，对已获得的资源保持不放
3. 不剥夺条件：进程已获得的资源，在未使用完之前，不能强行剥夺
4. 循环等待条件：若干进程之间形成一种头尾相接的循环等待资源关系



#####死锁产生原因
运行代码时，会调用Deadlock的构造函数，定义一个新的A类变量a和另一个新的B类变量b。当线程t启动被调用时，它会在后台默默地调用run函数去使用a，b的资源。与此同时，t还会经过20000次循环等待之后执行a.methd(b)使用a，b的资源。因为synchronized关键字的作用，使得一个对象的一部分synchronized资源只能允许被一个线程访问。要是有其他线程访问该对象的这部分synchronized资源或者其他部分synchronized资源，都会被阻塞。

有了上述基本理论基础，就很容易明白死锁的产生了：当run函数用b.method(a)方法使b取访问a的资源数据，同一时刻的t线程使用a.method(b)方法使a取访问b的资源数据，这样资源a被占用着，run函数无法进行；而同时b资源被run占用，线程t无法使用，形成了资源被阻塞，而对已获得的资源保持不放。进程已获得的资源，在未使用完之前，不能强行剥夺，若干进程之间形成一种头尾相接的循环等待资源关系。

死锁关系如下图所示：




_ _ _

