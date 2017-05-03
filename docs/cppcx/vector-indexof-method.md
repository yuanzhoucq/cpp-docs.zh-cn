---
title: "Vector::IndexOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Vector::IndexOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Vector::IndexOf 方法"
ms.assetid: 4a965992-3858-4e3f-992a-b94c0580b2f7
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Vector::IndexOf 方法
在当前向量中搜索指定项，如果找到，则返回该项的索引。  
  
## 语法  
  
```  
  
virtual bool IndexOf(  
   T value,  
   unsigned int* index  
);  
```  
  
#### 参数  
 `value`  
 要查找的项。  
  
 `index`  
 如果找到参数 `value`，则为该项的从零开始的索引；否则，为 0。  
  
 如果该项目是 Vector 的第一个元素，或者未找到该项目，则 `index` 参数为 0。 如果返回值为 `true`，则表明找到该项目，并且它是第一个元素；否则，表示未找到该项目。  
  
## 返回值  
 如果找到指定项目，则为 `true`；否则，为 `false`。  
  
## 备注  
 IndexOf 使用 std::find\_if 查找该项目。 因此，自定义元素类型应该重载 \=\= 和 \!\= 运算符以支持 find\_if 所需的相等性比较。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Vector 类](../cppcx/platform-collections-vector-class.md)