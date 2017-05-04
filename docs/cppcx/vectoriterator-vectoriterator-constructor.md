---
title: "VectorIterator::VectorIterator 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::VectorIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::VectorIterator 构造函数"
ms.assetid: 93286731-9499-4bfb-a24b-b302479c38cc
caps.latest.revision: 6
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::VectorIterator 构造函数
初始化 VectorIterator 类的新实例。  
  
## 语法  
  
```  
  
VectorIterator();  
  
explicit VectorIterator(  
   Windows::Foundation::Collections::IVector<T>^ v  
);  
```  
  
#### 参数  
 `v`  
 一个 IVector\<T\> 对象。  
  
## 备注  
 第一个语法示例是默认构造函数。 第二个语法示例是用于从 IVector\<T\> 对象构造 VectorIterator 的显式构造函数。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)