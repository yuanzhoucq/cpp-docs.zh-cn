---
title: "UnorderedMapView::UnorderedMapView 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::UnorderedMapView"
ms.assetid: 408aa6ca-dd8d-4946-a817-42a31d19f429
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::UnorderedMapView 构造函数
初始化 UnorderedMapView 类的新实例。  
  
## 语法  
  
```cpp  
  
UnorderedMapView();  
  
explicit UnorderedMapView(size_t n);  
  
UnorderedMapView(size_t n, const H& h);  
  
UnorderedMapView(size_t n, const H& h, const P& p);  
  
explicit UnorderedMapView(  
    const std::unordered_map<K, V, H, P>& m  
    );  
explicit UnorderedMapView(  
    std::unordered_map<K, V, H, P>&& m  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h,  
    const P& p  
    );  
  
UnorderedMapView(  
    std::initializer_list<std::pair<const K, V>> il  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h,  
    const P& p  
    );  
```  
  
#### 参数  
 n  
 要预分配空间的元素数目。  
  
 `InIt`  
 UnorderedMapView 的类型名称。  
  
 `H`  
 可以为键生成哈希值的函数对象。 默认为 `std::hash` 支持的类型的 [std::hash\<K\>](http://msdn.microsoft.com/zh-cn/54f67435-af9d-4217-a29d-fa4d2491a104)。  
  
 `P`  
 提供可比较两个键以确定其相等性的函数对象的类型。 默认为 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)。  
  
 `m`  
 对用于初始化 UnorderedMapView 的 [std::unordered\_map](../standard-library/unordered-map-class.md) 的引用或 [Lvalues 和 Rvalues](../Topic/Lvalues%20and%20Rvalues%20\(Visual%20C++\).md)。  
  
 `first`  
 用于初始化 UnorderedMapView 的一系列元素中的第一个元素的输入迭代器。  
  
 `last`  
 用于初始化 UnorderedMapView 的一系列元素之后的第一个元素的输入迭代器。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::UnorderedMapView 类](../cppcx/platform-collections-unorderedmapview-class.md)