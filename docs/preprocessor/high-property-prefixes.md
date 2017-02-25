---
title: "high_property_prefixes | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "high_property_prefixes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "high_property_prefixes 特性"
ms.assetid: 91c6cc2b-19b6-4aba-8831-d9e5cccb58b5
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# high_property_prefixes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 指定用于三个属性方法的备用前缀。  
  
## 语法  
  
```  
high_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### 参数  
 `GetPrefix`  
 要用于 **propget** 方法的前缀。  
  
 `PutPrefix`  
 要用于 **propput** 方法的前缀。  
  
 `PutRefPrefix`  
 要用于 **propputref** 方法的前缀。  
  
## 备注  
 默认情况下，高级别错误处理 **propget**、**propput** 和 **propputref** 方法分别由使用前缀 **Get**、`Put` 和 **PutRef** 命名的成员函数公开。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)