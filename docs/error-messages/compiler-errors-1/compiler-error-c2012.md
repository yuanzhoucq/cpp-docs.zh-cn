---
title: "编译器错误 C2012 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2012"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2012"
ms.assetid: 9f0d8162-c0b3-4234-a41f-836fdb75c84e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2012
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在“\<”之后缺少名称  
  
 `#include` 指令缺少必需的文件名。  
  
 以下示例生成 C2012：  
  
```  
// C2012.cpp #include <   // C2012 include the filename to resolve  
```  
  
 可能的解决方法：  
  
```  
// C2012b.cpp // compile with: /c #include <stdio.h>  
```