---
title: "vector&lt;bool&gt;::reference::operator bool | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "operatorbool"
  - "vector<bool>::reference::operatorbool"
  - "bool"
  - "std::vector<bool>::reference::operatorbool"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BOOL 运算符"
  - "reference::operator bool"
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
caps.latest.revision: 20
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vector&lt;bool&gt;::reference::operator bool
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

提供从 `vector<bool>::reference` 到 `bool` 的隐式转换。  
  
## 语法  
  
```  
operator bool( ) const;  
```  
  
## 返回值  
 [vector\<bool\>](../standard-library/vector-bool-class.md) 对象元素的布尔值。  
  
## 备注  
 `vector<bool>` 对象无法通过此运算符修改。  
  
## 要求  
 **标头：**\<vector\>  
  
 **命名空间:**  std  
  
## 请参阅  
 [vector\<bool\>::reference 类](../standard-library/vector-bool-reference-class.md)   
 [标准模板库](../misc/standard-template-library.md)