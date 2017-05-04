---
title: "UnorderedMap::HasKey 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::HasKey"
ms.assetid: 7c397cdc-82f6-470a-8a3c-f5ba2cc58ed6
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::HasKey 方法
确定当前 UnorderedMap 中是否包含指定键。  
  
## 语法  
  
```scr  
  
bool HasKey(  
   K key  
);  
```  
  
#### 参数  
 `key`  
 用于定位 UnorderedMap 元素的键。`key` 的类型名称为 *K*。  
  
## 返回值  
 如果找到该键，则为 `true`；否则为 `false`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections  
  
## 请参阅  
 [Platform::Collections::UnorderedMap 类](../cppcx/platform-collections-unorderedmap-class.md)   
 [集合](../cppcx/collections-c-cx.md)   
 [Windows::Foundation::Collections::IKeyValuePair\<K,V\>](http://msdn.microsoft.com/library/windows/apps/br226031.aspx)