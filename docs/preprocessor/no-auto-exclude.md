---
title: "no_auto_exclude | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_auto_exclude"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_auto_exclude 特性"
ms.assetid: 3241ef9c-758a-4e86-bdc5-37da6072430f
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# no_auto_exclude
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 禁用自动排除。  
  
## 语法  
  
```  
no_auto_exclude  
```  
  
## 备注  
 类型库可能包含在系统标头文件或其他类型库中定义的项的定义。  `#import` 尝试通过自动排除此类项来避免多个定义错误。  此操作完成后，将针对每个要排除的项发布 [编译器警告（等级 3）C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md)。  您可以使用此特性来禁用此自动排除。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)