---
title: "InputIterator::operator++ 运算符 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::InputIterator::operator++"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InputIterator::operator++ 运算符"
ms.assetid: 50781585-7a12-4f02-bff8-68fe0adf0693
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# InputIterator::operator++ 运算符
递增当前 InputIterator。  
  
## 语法  
  
```  
  
InputIterator& operator++();  
  
InputIterator operator++(  
   int  
);  
```  
  
## 返回值  
 第一个语法先递增然后返回当前 InputIterator。 第二个语法先返回当前 InputIterator 的副本然后递增当前 InputIterator。  
  
## 备注  
 第一个 InputIterator 预先递增当前 InputIterator。  
  
 第二个语法后递增当前 InputIterator。 第二个语法中的 `int` 类型指示后递增操作，而不是实际整数操作数。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::InputIterator 类](../cppcx/platform-collections-inputiterator-class.md)