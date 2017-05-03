---
title: "Vector::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::First 方法"
ms.assetid: ca6b7b55-dd49-4346-bfa4-d8010b228d44
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::First 方法
返回指向该向量中第一个元素的迭代器。  
  
## 语法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator <T>^   
   First();  
```  
  
## 返回值  
 指向该向量中第一个元素的迭代器。  
  
## 备注  
 保留 First\(\) 返回的迭代器的一种简便方式是将返回值分配给用 [auto](../Topic/auto%20\(C++\).md) 类型推导关键字声明的变量。 例如 `auto x = myVector->First();`。 此迭代器知道该集合的长度。  
  
 当你需要一对要传递到 STL 函数的迭代器时，请使用自由格式函数 [Windows::Foundation::Collections::begin](../cppcx/begin-function.md) 和 [Windows::Foundation::Collections::end](../cppcx/end-function.md)  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)   
 [集合](../cppcx/collections-c-cx.md)