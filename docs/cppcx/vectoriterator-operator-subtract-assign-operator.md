---
title: "VectorIterator::operator-= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator-="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator-= 运算符"
ms.assetid: 30bcf93c-4760-410d-b344-09741be10069
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator-= 运算符
按指定偏移量递减当前 VectorIterator。  
  
## 语法  
  
```  
VectorIterator& operator-=(  
   difference_type n  
);  
```  
  
#### 参数  
 `n`  
 整数偏移。  
  
## 返回值  
 更新的 VectorIterator。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)