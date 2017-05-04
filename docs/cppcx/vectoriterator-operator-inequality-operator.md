---
title: "VectorIterator::operator!= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorIterator::operator!="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorIterator::operator!= 运算符"
ms.assetid: 88b71c7e-9c88-4282-a518-455059da16c2
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorIterator::operator!= 运算符
指示当前 VectorIterator 是否不等于指定的 VectorIterator。  
  
## 语法  
  
```  
bool operator!=(  
   const VectorIterator& other  
) const;  
```  
  
#### 参数  
 `other`  
 另一 VectorIterator。  
  
## 返回值  
 如果当前 VectorIterator 不等于 `other`，则为 `true`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::VectorIterator 类](../cppcx/platform-collections-vectoriterator-class.md)