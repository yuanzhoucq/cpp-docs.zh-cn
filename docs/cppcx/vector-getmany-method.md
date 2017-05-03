---
title: "Vector::GetMany 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::GetMany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::GetMany 方法"
ms.assetid: e2d5ccf4-101a-47e5-a0d8-56f65a7ff28d
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::GetMany 方法
检索当前向量中的项序列，从指定的索引开始，并将它们复制到调用方分配的数组中。  
  
## 语法  
  
```  
  
virtual unsigned int GetMany(  
   unsigned int startIndex,   
   ::Platform::WriteOnlyArray<T>^ dest  
);  
```  
  
#### 参数  
 `startIndex`  
 要检索的项开头从零开始的索引。  
  
 `dest`  
 调用方分配的项数组，以由 `startIndex` 指定的元素开始，以向量中最后一个元素结尾。  
  
## 返回值  
 已检索的项的数量。  
  
## 备注  
 此函数并非旨在由客户端代码直接使用。 在 [to\_vector Function](../cppcx/to-vector-function.md) 中内部使用它以支持 Platform::Vector 实例到 std::vector 实例的高效转换。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)