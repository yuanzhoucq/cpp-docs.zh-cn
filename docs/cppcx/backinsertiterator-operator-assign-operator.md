---
title: "BackInsertIterator::operator= 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::BackInsertIterator::operator="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BackInsertIterator::operator= 运算符"
ms.assetid: 509c9b4c-14fb-4318-bf65-b8926cc72f4f
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# BackInsertIterator::operator= 运算符
将指定对象追加到当前有序集合的末尾。  
  
## 语法  
  
```  
  
BackInsertIterator& operator=(  
   const T& t  
);  
```  
  
#### 参数  
 `t`  
 要追加到当前集合的对象。  
  
## 返回值  
 对当前 BackInsertIterator 的引用。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::BackInsertIterator 类](../cppcx/platform-collections-backinsertiterator-class.md)