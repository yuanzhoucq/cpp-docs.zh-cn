---
title: "Vector::InsertAt 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::InsertAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::InsertAt"
ms.assetid: 05b2ca08-234e-4fc0-acfd-cafa148d1577
caps.latest.revision: 2
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::InsertAt 方法
在当前 Vector 中由指定的索引标识的元素后面插入指定的项。  
  
## 语法  
  
```  
  
virtual void InsertAt(  
   unsigned int index,   
   T item)  
```  
  
#### 参数  
 `index`  
 从零开始的无符号整数，用于指定 Vector 对象中的特定元素。  
  
 `item`  
 要插入到 Vector 中由 `index` 指定的元素后面的项。`item` 的类型由 *T* 类型名称定义。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)