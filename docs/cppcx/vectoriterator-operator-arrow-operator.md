---
title: "VectorIterator::operator-&gt; 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator->"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator-> 运算符"
ms.assetid: d6caed5c-4899-45f8-95a2-687eafeeb8e1
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator-&gt; 运算符
检索当前 VectorIterator 引用的元素的地址。  
  
## 语法  
  
```  
Detail::ArrowProxy<T> operator->() const;  
```  
  
## 返回值  
 当前 VectorIterator 引用的元素的值。  
  
 返回值的类型是此运算符的实现所需的未指定内部类型。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)