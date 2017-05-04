---
title: "VectorViewIterator::operator+ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator+"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator+ 运算符"
ms.assetid: 8206de2f-61b3-49cd-9715-d57695d880b3
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator+ 运算符
返回引用偏移指定 VectorViewIterator 指定偏移量处的元素的 VectorViewIterator。  
  
## 语法  
  
```  
  
VectorViewIterator operator+(  
   difference_type n  
) const;  
  
template <  
   typename T  
>   
inline VectorViewIterator<T> operator+  
   (ptrdiff_t n,   
   const VectorViewIterator<T>& i  
);  
  
```  
  
#### 参数  
 `T`  
 在第二个语法中，VectorViewIterator 的类型名称。  
  
 `n`  
 整数偏移。  
  
 `i`  
 在第二个语法，一个 VectorViewIterator。  
  
## 返回值  
 在第一个语法中，引用偏移当前 VectorViewIterator 指定偏移量处的元素的 VectorViewIterator。  
  
 在第二个语法中，引用偏移参数 `i` 开头指定偏移量处的元素的 VectorViewIterator。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)