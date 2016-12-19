---
title: "inject_statement | Microsoft Docs"
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
  - "inject_statement"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "inject_statement 特性"
ms.assetid: 07d6f0f4-d9fb-4e18-aa62-f235f142ff5e
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# inject_statement
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**C\+\+ 专用**  
  
 将其参数作为源文本插入类型库标头。  
  
## 语法  
  
```  
inject_statement("source_text")  
```  
  
#### 参数  
 `source_text`  
 要插入类型库标头文件的源文本。  
  
## 备注  
 该文本放置在用于将类型库内容包装在标头文件中的命名空间声明的开头。  
  
 **结束 C\+\+ 专用**  
  
## 请参阅  
 [\#import 特性](../preprocessor/hash-import-attributes-cpp.md)   
 [\#import 指令](../preprocessor/hash-import-directive-cpp.md)