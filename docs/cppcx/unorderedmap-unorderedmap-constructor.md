---
title: "UnorderedMap::UnorderedMap 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/25/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::UnorderedMap"
ms.assetid: bd62e663-7f3a-43ef-ad6d-8266128c778b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::UnorderedMap 构造函数
初始化 UnorderedMap 类的新实例。  
  
## 语法  
  
```scr  
UnorderedMap();  
  
  explicit UnorderedMap(  
      size_t n  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  explicit UnorderedMap(  
      const std::unordered_map<K, V, H, P>& m  
      );  
  
  explicit UnorderedMap(  
      std::unordered_map<K, V, H, P>&& m  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  UnorderedMap(std::initializer_list<  
      std::pair<const K, V>> il  
      );  
  
  UnorderedMap(::std::initializer_list<  
      std::pair<const K, V>> il,  
      size_t n  
      );  
  
  UnorderedMap(  
      ::std::initializer_list< ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(::std::initializer_list<  
      ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
```  
  
#### 参数  
 `InIt`  
 当前 UnorderedMap 的类型名称。  
  
 `P`  
 可比较两个键以确定它们是否相等的函数对象。 此参数默认为 [std::equal\_to\<K\>](../standard-library/equal-to-struct.md)。  
  
 `H`  
 可以为键生成哈希值的函数对象。 此参数默认为类支持的键类型的 [hash 类](../Topic/hash%20Class%201.md)。  
  
 `m`  
 对用于初始化当前 UnorderedMap 的 [std::unordered\_map](../standard-library/unordered-map-class.md) 的引用或 [Lvalues 和 Rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md)。  
  
 il  
 用于初始化映射的 [std::pair](../standard-library/initializer-list-class.md) 对象的 [std::initializer\_list](../standard-library/pair-structure.md)。  
  
 `first`  
 用于初始化当前 UnorderedMap 的一系列元素中的第一个元素的输入迭代器。  
  
 `last`  
 用于初始化当前 UnorderedMap 的一系列元素之后的第一个元素的输入迭代器。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections 命名空间](../cppcx/platform-collections-namespace.md)   
 [集合](../cppcx/collections-c-cx.md)