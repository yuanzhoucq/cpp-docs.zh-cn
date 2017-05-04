---
title: "BackInsertIterator::operator* 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::operator*"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::operator* 运算符"
ms.assetid: 68d70bc8-da84-49c6-ba35-4ac5aa6dad16
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::operator* 运算符
检索对当前 BackInsertIterator 的引用。  
  
## 语法  
  
```  
BackInsertIterator& operator*();  
```  
  
## 返回值  
 对当前 BackInsertIterator 的引用。  
  
## 备注  
 此运算符返回对当前 BackInsertIterator 的引用；而不是对当前集合中任何元素的引用。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::BackInsertIterator 类](../cppcx/platform-collections-backinsertiterator-class.md)