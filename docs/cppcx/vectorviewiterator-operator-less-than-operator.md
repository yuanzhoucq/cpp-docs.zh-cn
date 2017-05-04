---
title: "VectorViewIterator::operator&lt; 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorViewIterator::operator<"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorViewIterator::operator< 运算符"
ms.assetid: 411c9af9-78b1-4b1b-839b-3bec76020184
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorViewIterator::operator&lt; 运算符
指示当前 VectorIterator 是否小于指定的 VectorIterator。  
  
## 语法  
  
```  
bool operator<(  
   const VectorViewIterator& other  
) const;  
```  
  
#### 参数  
 `other`  
 另一 VectorIterator。  
  
## 返回值  
 如果当前 VectorIterator 小于 `true`，则为 `other`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorViewIterator 类](../cppcx/platform-collections-vectorviewiterator-class.md)