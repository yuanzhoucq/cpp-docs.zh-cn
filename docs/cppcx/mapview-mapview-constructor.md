---
title: "MapView::MapView 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::MapView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::MapView 构造函数"
ms.assetid: 67a3250c-b527-47ac-a103-0fd186046d71
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::MapView 构造函数
初始化 MapView 类的新实例。  
  
## 语法  
  
```  
explicit MapView(  
    const C& comp = C()  
    );  
  
explicit MapView(  
    const ::std::map<K, V, C>& m  
    );  
  
explicit MapView(  
    std::map<K, V, C>&& m  
    );  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C()  
    );  
  
MapView(::std::initializer_list<  
    std::pair<const K, V>> il,  
    const C& comp = C()  
    );  
```  
  
#### 参数  
 `InIt`  
 当前 MapView 的类型名称。  
  
 `comp`  
 可以将两个元素值作为排序键加以比较，以决定它们在 MapView 中的相对顺序的函数对象。  
  
 `m`  
 对用于初始化当前 MapView 的 [Lvalues 和 Rvalues](../Topic/Lvalues%20and%20Rvalues%20\(Visual%20C++\).md) 的引用或 [map 类](../standard-library/map-class.md)。  
  
 `first`  
 用于初始化当前 MapView 的一系列元素中的第一个元素的输入迭代器。  
  
 `last`  
 用于初始化当前 MapView 的一系列元素之后的第一个元素的输入迭代器。  
  
 il  
 其元素将插入 MapView 的 [std::initializer\_list\<std::pair\<K,V\>\>](../standard-library/initializer-list-class.md)。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::MapView 类](../cppcx/platform-collections-mapview-class.md)