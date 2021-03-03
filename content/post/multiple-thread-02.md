---
title: "Multiple Thread 02"
author: "zero"
date: 2021-01-22T20:41:48+09:00
categories: ["java"]
tags: ["Multiple Thread"]
archives: ["2021-01"]
draft: true
---
## Java のスレッド

### javaスレッドのlife cycle

![thread life cycle](/images/java-thread-life-cycle.png)
<!--more-->
### スレッドの生成方法

#### implements Runnable

* 実行結果を返却しない

#### extends Thread

* 実行結果を返却しない

#### Callable + Future or Callable + FutureTask

* 実行結果を返却する

* Callable + Future  sample code

```code
 public class CallableTask implements Callable<String> {
    @Override
    public String call() throws Exception {
        System.out.println(Thread.currentThread().getName() +" is running");
        return "execute end";
    }

    public static void main(String[] args) throws Exception {
        CallableTask callableTask = new CallableTask();
        // create execute service
        ExecutorService executorService = Executors.newFixedThreadPool(1);
        // submit
        Future<String> result = executorService.submit(callableTask);
        //get result
        System.out.println(result.get());
        //shutdown
        executorService.shutdown();

    }
}

```

[Future doc](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/util/concurrent/Future.html)

* Callable + FutureTask  sample code

```code
        ..........
        FutureTask<String> futureTask = new FutureTask<>(callableTask);
        new Thread(futureTask).start();
        System.out.println(futureTask.get());
```

[FutureTask doc](https://docs.oracle.com/en/java/javase/15/docs/api/java.base/java/util/concurrent/FutureTask.html)

### スレッドの停止

* フラグを設置する

### スレッドの通知と待ち

#### 待ち(wait())

* 呼び出したスレッドはそのオブジェクトのウェイトセットに入ります。
  * `注意` synchronized blockの中に呼び出す。
  * synchronized block以外のところから呼び出すすると、throw IllegalMonitorStateException

#### 通知(notify(),notifyAll())

* そのオブジェクトのウェイトセットにあるスレッドが1つ再開します。
  * 複数の場合、その中の一つを再開します。
  * `注意` synchronized blockの中に呼び出す。
