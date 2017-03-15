---
title: "no_implementation | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "no_implementation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "no_implementation 特性"
ms.assetid: bdc67785-e131-409c-87bc-f4d2f4abb07b
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# no_implementation
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 取消生成 .tli 标头，它包含包装器成员函数的实现。  
  
## 语法  
  
```  
no_implementation  
```  
  
## 备注  
 如果指定此特性，则将生成 .tlh 标头（带用于公开类型库项的声明），而无需用于包含 .tli 标头文件的 `#include` 语句。  
  
 此特性与 [implementation\_only](../preprocessor/implementation-only.md) 结合使用。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)