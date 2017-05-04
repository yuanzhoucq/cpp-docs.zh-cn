---
title: "VectorView::GetMany 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::GetMany"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::GetMany 方法"
ms.assetid: 67d9348f-66fe-417e-9e25-5de0a3cd306c
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::GetMany 方法
从当前 VectorView 检索项序列，从指定索引处开始。  
  
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
 此操作完成时的项列表，以由 `startIndex` 指定的元素开始，以 VectorView 中最后一个元素结尾。  
  
## 返回值  
 已检索的项的数量。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [VectorView Class](http://msdn.microsoft.com/zh-cn/79697692-ae58-40e0-958f-cf1be6347994)