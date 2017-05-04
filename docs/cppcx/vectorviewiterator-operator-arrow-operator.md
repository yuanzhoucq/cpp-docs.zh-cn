---
title: "VectorViewIterator::operator-&gt; 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator-> 运算符"
ms.assetid: cc02cfa2-dfcb-4fb7-b4a0-c290f91aa4a6
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator-&gt; 运算符
检索当前 VectorViewIterator 引用的元素的地址。  
  
## 语法  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
## 返回值  
 当前 VectorViewIterator 引用的元素的值。  
  
 返回值的类型是此运算符的实现所需的未指定内部类型。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)