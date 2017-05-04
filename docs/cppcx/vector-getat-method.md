---
title: "Vector::GetAt 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::GetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::GetAt 方法"
ms.assetid: 3766b399-cef2-4006-9a87-50f717390cac
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::GetAt 方法
检索由指定索引标识的当前向量的元素。  
  
## 语法  
  
```  
  
virtual T GetAt(  
   unsigned int index  
);  
```  
  
#### 参数  
 `index`  
 从零开始的无符号整数，用于指定 Vector 对象中的特定元素。  
  
## 返回值  
 `index` 参数指定的元素。 元素类型通过 *T* 类型名称定义。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)