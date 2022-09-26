title: java集合详解和之间关系
author: LZH
tags:
  - java
  - 集合
categories: []
date: 2019-04-20 03:42:00
---
# 1.java常用集合类家族史:

（具体请参照API[http://tool.oschina.net/apidocs/apidoc?api=jdk-zh](http://tool.oschina.net/apidocs/apidoc?api=jdk-zh)）
常用集合如太极一般，一分为二，一者曰Collection，再者曰Map。
话说，太极生两仪，两仪生四象。。。（布拉布拉。。。）
## Collection接口
其中Collection接口一般用到的就是List和Set两种（下面其他的也会涉及到不过以这两种为主）：
以上二者，List再生ArrayList/Vector/LinkedList，Set再生TreeSet/HashSet。
Collection--List--ArrayList
      |    |--Vecter
      |    |--LinkedList
      |--Set--HashSet
         |--TreeSet
（这几个用的多，但是辈分不一样，详看下图）
<!-- more -->
## Map接口（图）
Map接口最多的就是HashMap，其他的就是看看，平时一般用不到，除非很特殊的地方
![](集合框架体系1.jpg)
# 2.各自优点
![](集合框架体系3.png)
![](集合框架体系2.jpg)
## 接口
### 1.Collection 接口
Collection 是最基本的集合接口，一个 Collection 代表一组 Object，即 Collection 的元素, Java不提供直接继承自Collection的类，只提供继承于的子接口(如List和set)。
Collection 接口存储一组不唯一，无序的对象。
### 2.List 接口
List接口是一个有序的 Collection，使用此接口能够精确的控制每个元素插入的位置，能够通过索引(元素在List中位置，类似于数组的下标)来访问List中的元素，第一个元素的索引为 0，而且允许有相同的元素。
List 接口存储一组不唯一，有序（插入顺序）的对象。
### 3.Set 接口
Set 具有与 Collection 完全一样的接口，只是行为上不同，Set 不保存重复的元素。
Set 接口存储一组唯一，无序的对象。
### 4.SortedSet
继承于Set保存有序的集合。
### 5.Map
Map 接口存储一组键值对象，提供key（键）到value（值）的映射。
### 6.Map.Entry 
描述在一个Map中的一个元素（键/值对）。是一个Map的内部类。
### 7.SortedMap
继承于 Map，使 Key 保持在升序排列。

ps：对有序的理解
List有序和Set无序说的是啥呢？
就是呀，List是进去啥顺序，出来也是啥顺序。Set呢也想保证跟List一样的顺序的话是不行的，Set会自动去重（Set内心：就是不一样！能拿我怎么样！）。
这就有小伙伴说了，SortedSet不是也是有序的呀，这不是跟List一样啊！这么说就不对了，此有序非彼有序，SortedSet有序是因为他会自动排序！就是说，有序的概念有很多种比如正序倒序都是有序。

## 实现类

（太多了，列多点，其实看其中几个常用的就行了）
### 1.AbstractCollection
实现了大部分的集合接口。
### 2.AbstractList
继承于AbstractCollection 并且实现了大部分List接口。
### 3.AbstractSequentialList
继承于 AbstractList ，提供了对数据元素的链式访问而不是随机访问。
### 4.LinkedList
该类实现了List接口，允许有null（空）元素。主要用于创建链表数据结构，该类没有同步方法，如果多个线程同时访问一个List，则必须自己实现访问同步，解决方法就是在创建List时候构造一个同步的List。例如：
```
Listlist=Collections.synchronizedList(newLinkedList(...));
```
LinkedList 查找效率低。
### 5.ArrayList
该类也是实现了List的接口，实现了可变大小的数组，随机访问和遍历元素时，提供更好的性能。该类也是非同步的,在多线程的情况下不要使用。ArrayList 增长当前长度的50%，插入删除效率低。
### 6.AbstractSet 
继承于AbstractCollection 并且实现了大部分Set接口。
### 7.HashSet
该类实现了Set接口，不允许出现重复元素，不保证集合中元素的顺序，允许包含值为null的元素，但最多只能一个。
### 8.LinkedHashSet
具有可预知迭代顺序的 Set 接口的哈希表和链接列表实现。
### 9. TreeSet
该类实现了Set接口，可以实现排序等功能。
### 10.AbstractMap
实现了大部分的Map接口。
### 11.HashMap
HashMap 是一个散列表，它存储的内容是键值对(key-value)映射。
该类实现了Map接口，根据键的HashCode值存储数据，具有很快的访问速度，最多允许一条记录的键为null，不支持线程同步。
### 12.TreeMap 
继承了AbstractMap，并且使用一颗树。
### 13.WeakHashMap 
继承AbstractMap类，使用弱密钥的哈希表。
### 14.LinkedHashMap
继承于HashMap，使用元素的自然顺序对元素进行排序.
### 15.IdentityHashMap
继承AbstractMap类，比较文档时使用引用相等。
### java.util包中定义的类
#### Vector
该类和ArrayList非常相似，但是该类是同步的，可以用在多线程的情况，该类允许设置默认的增长长度，默认扩容方式为原来的2倍。
#### Stack
栈是Vector的一个子类，它实现了一个标准的后进先出的栈。
#### Dictionary
Dictionary 类是一个抽象类，用来存储键/值对，作用和Map类相似。
#### Hashtable
Hashtable 是 Dictionary(字典) 类的子类，位于 java.util 包中。
#### Properties 
Properties 继承于 Hashtable，表示一个持久的属性集，属性列表中每个键及其对应值都是一个字符串。
#### BitSet
一个Bitset类创建一种特殊类型的数组来保存位值。BitSet中数组大小会随需要增加。
# 针对几个常用实现类进行详细分析
1.List/ArrayList/LinkedList/vector
2.Set/HashSet/TreeSet
3.HashMap/TreeMap/HashTable
