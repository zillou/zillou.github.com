---
layout: post
title: "理解Ruby中的Symbol"
description: "Symbol是Ruby中最让我费解的概念之一，直到我读到Russ Olsen的解释，Symbol就是另一种字符串，优化来做代表某物的名字，Symbol就是Symbol，就是指代某物的符号。"
category: programming
tags: [ruby, symbol]
---
{% include JB/setup %}

最近在看Russ Olsen写的*[Eloquent Ruby](http://book.douban.com/subject/6052175/)*。目前让我印象最深刻的一章是第六章-
Use Symbols to Stand for Something。本人也是刚刚开始自学Ruby，Ruby中很多较新的概念我都没法完全理解。相信也有很多人对Symbol的概念不太清晰，即使平时知道怎么用，也讲不出来Symbol的奥妙，不过看了Russ的解释后，你就一定清楚什么是Symbol，为什么要有Symbol，以及Ruby中的Symbol为什么是这个样子。


## Symbol就是String!

一个符号就是字符或者字符串。不管是`"dog"`还是`:dog`都是由一个d、一个o和一个g三个字母构成。实际上在Ruby中，两者之间不仅可以相互转换，有些时候甚至是可以等效的。
比如在ActionRecord中`book = Book.find(:all)`也可以写出`book = Book.find('all')`。

那么为什么Ruby中要分出Symbol和字符串呢？

## 字符的两种用法

答案是我们平时代码中使用字符串(strings of characters)有主要有两种很不一样的目的:

1. 表示字符数据，比如地址、名字。
2. 仅仅用作名字，比如某种状态，如"active"或者"cancelled"。


第一种情况的时候，字符本身是重要的，也有操作这些作为数据的字符的需要；而第二种情况，这个名字中的字符本身是不重要的(你也可以用1来表示Active的状态，用0来表示Cancelled的状态)，所以就没有必要去操作这种情况中的字符了。


## Symbol，一切皆为代表

所以，显而易见的，String就是用作字符数据的数据类型，而仅仅需要表示一个名字，就是Symbol出场的时候了。

Ruby中的String的设计是为了处理字符数据的方便；而Symbol的一切设计都是基于用Symbol来作为一个名字，代表某物这个宗旨的。

所以也就很容易理解Symbol的特性了：

##### 1. 一个Symbol只有一个实例

    a = :active
    b = :active
    b = c

这段代码中a, b, c其实都是指向同一个对象。

##### 2.Symbol不可变

我们知道Symbol创建好之后就不能再对其进行修改的操作了。因为我们也没有必要在运行中去为一个东西改名字。所以你一旦创建好一个叫`:active`的Symbol之后，你不能也不需要在它的生命周期中去改变它。

