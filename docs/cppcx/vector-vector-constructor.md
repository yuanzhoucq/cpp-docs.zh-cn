---
title: "Vector::Vector 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::Vector"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::Vector 构造函数"
ms.assetid: 5454433d-e206-45ea-bc8b-bb5a7bf38c17
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::Vector 构造函数
初始化 Vector 类的新实例。  
  
## 语法  
  
```  
Vector();  
  
explicit Vector(  
    unsigned int size  
    );  
  
Vector(  
    unsigned int size,  
    T value  
    );  
  
template <typename U> explicit Vector(  
    const ::std::vector<U>& v  
    );  
  
template <typename U> explicit Vector(  
    std::vector<U>&& v  
    );  
  
Vector(  
    const T * ptr,  
    unsigned int size  
    );  
  
template <size_t N> explicit Vector(  
    const T(&arr)[N]  
    );  
  
template <size_t N> explicit Vector(  
    const std::array<T, N>& a  
    );  
  
explicit Vector(  
    const Array<T>^ arr  
    );  
  
template <typename InIt> Vector(  
    InIt first,  
    InIt last  
    );  
  
Vector(  
    std::initializer_list<T> il  
    );  
```  
  
#### 参数  
 a  
 用于初始化 Vector 的 [std::array](../standard-library/array-class-stl.md)。  
  
 a  
 用于初始化 Vector 的 [Platform::Array](../cppcx/platform-array-class.md)。  
  
 `InIt`  
 用于初始化当前向量的对象集合的类型。  
  
 il  
 用于初始化 Vector 的 `T` 类型的对象的 [std::initializer\_list](../standard-library/initializer-list-class.md)。  
  
 `N`  
 用于初始化当前向量的对象集合中的元素数。  
  
 `size`  
 向量中元素的数目。  
  
 `value`  
 用于初始化当前向量中每个元素的值。  
  
 `v`  
 对用于初始化当前 Vector 的 [std::vector](../Topic/vector%20Class%201.md) 的 [Lvalues 和 Rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md)。  
  
 `ptr`  
 指向用于初始化当前向量的 `std::vector` 的指针。  
  
 `arr`  
 用于初始化当前向量的 [Platform::Array](../cppcx/platform-array-class.md) 对象。  
  
 `a`  
 用于初始化当前向量的 [std::array](../Topic/vector%20Class%201.md) 对象。  
  
 `first`  
 用于初始化当前向量的对象序列中的第一个元素。`first` 的类型通过完美转发传递。 有关更多信息，请参见[规则引用声明符：&&](~/cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 `last`  
 用于初始化当前向量的对象序列中的最后一个元素。`last` 的类型通过完美转发传递。 有关更多信息，请参见[规则引用声明符：&&](~/cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)   
 [集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)