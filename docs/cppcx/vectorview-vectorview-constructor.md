---
title: "VectorView::VectorView 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::VectorView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::VectorView 构造函数"
ms.assetid: 5ec14dbc-5f6f-44b6-8fc4-f5a31053eb5f
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::VectorView 构造函数
初始化 VectorView 类的新实例。  
  
## 语法  
  
```  
VectorView();  
explicit VectorView(  
   UInt32 size  
);  
VectorView(  
   UInt32 size,  
   T value  
);  
explicit VectorView(  
   const ::std::vector<T>& v  
);  
explicit VectorView(  
   ::std::vector<T>&& v  
);  
VectorView(  
   const T * ptr,  
   UInt32 size  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const T (&arr)[N]  
);  
  
template <  
   size_t N  
>  
explicit VectorView(  
   const ::std::array<T,  
   N>& a  
);  
  
explicit VectorView(  
   const ::Platform::Array<T>^ arr  
);  
  
template <  
   typename InIt  
>  
VectorView(  
   InItfirst,  
   InItlast  
);  
  
VectorView(  
   std::initializer_list<T> il  
);  
```  
  
#### 参数  
 `InIt`  
 用于初始化当前 VectorView 的对象集合的类型。  
  
 il  
 其中元素将用于初始化 VectorView 的 [std::initializer\_list](../standard-library/initializer-list-class.md)。  
  
 `N`  
 用于初始化当前 VectorView 的对象集合中元素的数量。  
  
 `size`  
 VectorView 中元素的数量。  
  
 `value`  
 用于初始化当前 VectorView 中每个元素的值。  
  
 `v`  
 对用于初始化当前 VectorView 的 [::std::vector](../Topic/vector%20Class%201.md) 的 [Lvalues 和 Rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md)。  
  
 `ptr`  
 指向用于初始化当前 VectorView 的 `std::vector` 的指针。  
  
 `arr`  
 用于初始化当前 VectorView 的 [Platform::Array](../cppcx/platform-array-class.md) 对象。  
  
 `a`  
 用于初始化当前 VectorView 的 [std::array](../Topic/vector%20Class%201.md) 对象。  
  
 `first`  
 用于初始化当前 VectorView 的对象序列中的第一个元素。`first` 的类型通过完美转发传递。 有关详细信息，请参阅[规则引用声明符：&&](~/cpp/rvalue-reference-declarator-amp-amp.md)。  
  
 `last`  
 用于初始化当前 VectorView 的对象序列中的最后一个元素。`last` 的类型通过完美转发传递。 有关更多信息，请参见[规则引用声明符：&&](~/cpp/rvalue-reference-declarator-amp-amp.md)。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)