---
title: "错误 C1104 | Microsoft Docs"
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
  - "C1104"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1104"
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 错误 C1104
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导入 libid 时遇到错误：“message”  
  
 导入类型库时编译器检测到问题。  例如，你不能使用 libid 指定类型库，同时还指定 `no_registry`。  
  
 有关更多信息，请参见[\#import 指令](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下面的示例生成 C1104：  
  
```  
// C1104.cpp #import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104  
```