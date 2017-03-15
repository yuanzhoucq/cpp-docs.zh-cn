---
title: "no_smart_pointers | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_search_pointers"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_smart_pointers 特性"
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# no_smart_pointers
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 取消对类型库中所有接口的智能指针的创建。  
  
## 语法  
  
```  
no_smart_pointers  
```  
  
## 备注  
 默认情况下，当使用 `#import` 时，您将获得针对类型库中的所有接口的智能指针声明。  这些智能指针的类型为 [\_com\_ptr\_t 类](../cpp/com-ptr-t-class.md)。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)