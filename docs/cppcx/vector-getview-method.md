---
title: "Vector::GetView 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::GetView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::GetView 方法"
ms.assetid: dad9f0b5-b75e-4b20-b63f-40d09591dcd5
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::GetView 方法
返回向量的只读视图，即 IVectorView。  
  
## 语法  
  
```  
  
Windows::Foundation::Collections::IVectorView<T>^   
   GetView();  
```  
  
## 返回值  
 一个 IVectorView 对象。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)