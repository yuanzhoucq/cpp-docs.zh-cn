---
title: "Map::First 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::First"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::First 方法"
ms.assetid: bb1a4458-ecc3-43b0-b808-1693f853ad82
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::First 方法
返回指定映射中第一个元素的迭代器，如果映射为空，则返回 `nullptr`。  
  
## 语法  
  
```  
  
virtual Windows::Foundation::Collections::IIterator<  
Windows::Foundation::Collections::IKeyValuePair<K, V>^>^ First();  
```  
  
## 返回值  
 指定映射中第一个元素的迭代器。  
  
## 备注  
 保留 First\(\) 返回的迭代器的一种简便方式是将返回值分配给用 [auto](~/cpp/auto-cpp.md) 类型推导关键字声明的变量。 例如 `auto x = myMap->First();`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::Map 类](../cppcx/platform-collections-map-class.md)   
 [集合 \(C\+\+\/CX\)](../cppcx/collections-c-cx.md)