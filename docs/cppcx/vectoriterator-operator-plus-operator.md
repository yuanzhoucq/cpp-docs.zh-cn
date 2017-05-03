---
title: "VectorIterator::operator+ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator+"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator+ 运算符"
ms.assetid: 5e907537-7d10-4766-a412-e7ea08b3456a
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator+ 运算符
返回引用偏移指定 VectorIterator 指定偏移量处的元素的 VectorIterator。  
  
## 语法  
  
```  
  
VectorIterator operator+(  
   difference_type n) ;  
  
template <  
   typename T  
>  
inline VectorIterator<T> operator+(  
   ptrdiff_t n,  
   const VectorIterator<T>& i  
);  
  
```  
  
#### 参数  
 `T`  
 在第二个语法中，VectorIterator 的类型名称。  
  
 `n`  
 整数偏移。  
  
 `i`  
 在第二个语法，一个 VectorIterator。  
  
## 返回值  
 在第一个语法中，引用偏移当前 VectorIterator 指定偏移量处的元素的 VectorIterator。  
  
 在第二个语法中，引用偏移参数 `i` 开头指定偏移量处的元素的 VectorIterator。  
  
## 备注  
 第一个语法示例  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [\(NOTINBUILD\) Platform 命名空间](http://msdn.microsoft.com/zh-cn/f3ce3eab-028c-4204-ba9f-9ab8af17c8c4)