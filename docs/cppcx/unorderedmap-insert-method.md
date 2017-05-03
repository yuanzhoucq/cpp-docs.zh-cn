---
title: "UnorderedMap::Insert 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::Insert"
ms.assetid: 89d55301-3cad-4877-825b-35096a1dd740
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::Insert 方法
将指定的键值对添加到当前 UnorderedMap 对象中。  
  
## 语法  
  
```cpp  
  
virtual bool Insert(  
   K key,   
   V value  
);  
```  
  
#### 参数  
 `key`  
 键值对中的键部分。`key` 的类型名称为 *K*。  
  
 `value`  
 键值对中的值部分。`value` 的类型名称为 *V*。  
  
## 返回值  
 如果当前映射中一个现有元素的键匹配 `true` 并且该元素的值部分设置为 `key`，则为 `value`。 如果当前 Map 中没有任何现有元素匹配 `false` 并且 `key` 和 `key` 参数构成键值对并随后添加到当前 UnorderedMap 中，则为 `value`。  
  
## 要求  
 **标头：**collection.h  
  
 **命名空间：**Platform::Collections