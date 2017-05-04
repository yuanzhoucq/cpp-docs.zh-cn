---
title: "InputIterator::operator== 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator::operator=="
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator::operator== 运算符"
ms.assetid: 84f1b69a-77b9-467c-ad1a-2fe8a7c3009e
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# InputIterator::operator== 运算符
指示当前 InputIterator 是否等于指定的 InputIterator。  
  
## 语法  
  
```  
bool operator==(  
   const InputIterator& other  
) const;  
```  
  
#### 参数  
 `other`  
 另一个 InputIterator。  
  
## 返回值  
 如果当前 InputIterator 等于 `true`，则为 `other`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::InputIterator 类](../cppcx/platform-collections-inputiterator-class.md)