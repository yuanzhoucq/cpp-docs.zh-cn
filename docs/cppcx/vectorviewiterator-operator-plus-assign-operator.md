---
title: "VectorViewIterator::operator+= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator+="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator+= 运算符"
ms.assetid: 2009e54e-a4f2-444a-b729-a1b6b8b707bb
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator+= 运算符
按指定偏移量递增当前 VectorViewIterator。  
  
## 语法  
  
```  
VectorViewIterator& operator+=(  
   difference_type n  
);  
```  
  
#### 参数  
 `n`  
 整数偏移。  
  
## 返回值  
 更新的 VectorViewIterator。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)