---
title: "VectorView::IndexOf 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::IndexOf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::IndexOf 方法"
ms.assetid: 848117ec-ad4a-4a0b-9c1e-9076e5188869
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::IndexOf 方法
在当前 VectorView 中搜索指定项，如果找到，则返回该项的索引。  
  
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
  
 如果该项目是 VectorView 的第一个元素，或者未找到该项目，则 `index` 参数为 0。 如果返回值为 `true`，则表明找到该项目，并且它是第一个元素；否则，表示未找到该项目。  
  
## 返回值  
 如果找到指定项目，则为 `true`；否则，为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [VectorView Class](http://msdn.microsoft.com/zh-cn/79697692-ae58-40e0-958f-cf1be6347994)