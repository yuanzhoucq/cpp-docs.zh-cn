---
title: "VectorViewIterator::operator&gt;= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator>="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator>= 运算符"
ms.assetid: 506fbf12-a28f-4695-a5a4-418341dec806
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&gt;= 运算符
指示当前 VectorViewIterator 是否大于或等于指定的 VectorViewIterator。  
  
## 语法  
  
```  
  
bool operator>=(  
   const VectorViewIterator& other  
) const;  
```  
  
#### 参数  
 `other`  
 另一 VectorViewIterator。  
  
## 返回值  
 如果当前 VectorViewIterator 大于或等于 `true`，则为 `other`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)