---
title: "raw_property_prefixes | Microsoft Docs"
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
  - "raw_property_prefixes"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "raw_property_prefixes 特性"
ms.assetid: 03a0f48c-c460-4175-a762-9f7f8d84b12f
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raw_property_prefixes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 指定用于三个属性方法的备用前缀。  
  
## 语法  
  
```  
raw_property_prefixes("GetPrefix","PutPrefix","PutRefPrefix")  
```  
  
#### 参数  
 `GetPrefix`  
 要用于 **propget** 方法的前缀。  
  
 `PutPrefix`  
 要用于 **propput** 方法的前缀。  
  
 `PutRefPrefix`  
 要用于 **propputref** 方法的前缀。  
  
## 备注  
 默认情况下，低级别 **propget**、**propput** 和 **propputref** 方法分别由使用前缀 **get\_**、**put\_** 和 **putref\_** 命名的成员函数公开。  这些前缀与在 MIDL 生成的标头文件中使用的名称兼容。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)