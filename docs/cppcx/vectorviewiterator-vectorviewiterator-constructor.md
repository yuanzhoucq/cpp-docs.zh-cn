---
title: "VectorViewIterator::VectorViewIterator 构造函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::VectorViewIterator"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::VectorViewIterator 构造函数"
ms.assetid: 30bf643a-4100-4547-b34c-ce16c89f78ed
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::VectorViewIterator 构造函数
初始化 VectorViewIterator 类的新实例。  
  
## 语法  
  
```  
  
VectorViewIterator();  
  
explicit VectorViewIterator(  
   Windows::Foundation::Collections::IVectorView<T>^ v  
);  
```  
  
#### 参数  
 `v`  
 一个 IVectorView\<T\> 对象。  
  
## 备注  
 第一个语法示例是默认构造函数。 第二个语法示例是用于从 IVectorView\<T\> 对象构造 VectorViewIterator 的显式构造函数。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)