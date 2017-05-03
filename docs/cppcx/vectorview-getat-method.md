---
title: "VectorView::GetAt 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::VectorView::GetAt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "VectorView::GetAt 方法"
ms.assetid: 01c5feda-2a97-4429-ae15-4aced96ce332
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# VectorView::GetAt 方法
检索由指定的索引表示的当前 VectorView 的元素。  
  
## 语法  
  
```  
  
T GetAt(  
   UInt32 index  
);  
```  
  
#### 参数  
 `index`  
 从零开始的无符号整数，用于指定 VectorView 对象中的特定元素。  
  
## 返回值  
 `index` 参数指定的元素。 元素类型由 VectorView 模板参数 *T* 指定。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [VectorView Class](http://msdn.microsoft.com/zh-cn/79697692-ae58-40e0-958f-cf1be6347994)