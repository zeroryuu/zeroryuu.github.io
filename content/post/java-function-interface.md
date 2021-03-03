---
title: "Java Function Interface"
author: "zero"
date: 2021-01-15T22:56:32+09:00
categories: ["java"]
tags: ["function"]
archives: ["2021-01"]
draft: true
---
## 定義

`定義されている抽象メソッドが1つだけあるインターフェース。`

privateメソッド、staticメソッドやデフォルトメソッドは含まれていても構わない
関数型インターフェースの条件を満たしたインターフェースであれば、自動的に関数型インターフェースとして使用できる。
FunctionalInterfaceアノテーションを付けていると、関数型インターフェースの条件を満たしていない場合にコンパイルエラーになってくれる。

<!--more-->

## 関数型インターフェースの使用

* メソッドのパラメータ
* メソッドの戻り型

## 関数型インターフェースの分類

### Supplier（get）系

* 引数なしで、結果のサプライヤを表します。

### Function（apply）系

* 1つの引数を受け取って結果を生成する関数を表します。

### Consumer（accept）系

* 単一の入力引数を受け取って結果を返さないオペレーションを表します。

### Predicate（test）系

* 1つの引数の述語(boolean値関数)を表します。

### 関数型インターフェースの詳細

![java.util.function](/images/java-util-function.png)

[Package java.util.function](https://docs.oracle.com/javase/8/docs/api/java/util/function/package-summary.html)
