---
title: "VectorView::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::First 方法"
ms.assetid: 543a5c5b-8ce3-4be3-9fad-726928de7855
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::First 方法
返回指定 VectorView 中的第一个元素的迭代器。  
  
## 语法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<T>^   
   First();  
```  
  
## 返回值  
 指定 VectorView 中第一个元素的迭代器。  
  
## 备注  
 保留 First\(\) 返回的迭代器的一种简便方式是将返回值分配给用 [auto](~/cpp/auto-cpp.md) 类型推导关键字声明的变量。 例如 `auto x = myVectorView->First();`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [VectorView Class](http://msdn.microsoft.com/zh-cn/79697692-ae58-40e0-958f-cf1be6347994)