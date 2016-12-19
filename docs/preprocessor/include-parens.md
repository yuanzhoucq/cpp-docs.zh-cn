---
title: "include() | Microsoft Docs"
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
  - "include()"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "include() 特性"
ms.assetid: 86c9dcb2-d9e0-4fd5-97d7-0bb3e23d6ecc
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# include()
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 禁用自动排除。  
  
## 语法  
  
```  
include("Name1"[,"Name2", ...])  
```  
  
#### 参数  
 `Name1`  
 要强制包含的第一项。  
  
 `Name2`  
 要强行包含的第二项（如果需要）。  
  
## 备注  
 类型库可能包含在系统标头文件或其他类型库中定义的项的定义。  `#import` 尝试通过自动排除此类项来避免多个定义错误。  如果已排除项（如 [编译器警告（等级 3）C4192](../error-messages/compiler-warnings/compiler-warning-level-3-c4192.md) 所示），但不应这样做，则可使用此特性禁用自动排除。  此特性可采用任意数量的参数，每个参数都是要包含的类型库项的名称。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)