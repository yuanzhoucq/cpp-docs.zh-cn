---
title: "exclude (#import) | Microsoft Docs"
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
  - "exclude"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "exclude 特性"
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# exclude (#import)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 从要生成的类型库标头文件中排除项。  
  
## 语法  
  
```  
exclude("Name1"[, "Name2",...])  
```  
  
#### 参数  
 `Name1`  
 要排除的第一项。  
  
 `Name2`  
 要排除的第二项（如果需要）。  
  
## 备注  
 类型库可能包含在系统标头文件或其他类型库中定义的项的定义。  此特性可以采用任意数量的参数，每个参数都是要排除的顶级类型库项。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)