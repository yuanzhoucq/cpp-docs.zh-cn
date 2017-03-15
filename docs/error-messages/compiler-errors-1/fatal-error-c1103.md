---
title: "错误 C1103 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C1103"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1103"
ms.assetid: 9d276939-9c47-4235-9d20-76b8434f9731
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 错误 C1103
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

导入 progid 时遇到错误：“message”  
  
 导入类型库时编译器检测到问题。  例如，你不能使用 progid 指定类型库，同时还指定 `no_registry`。  
  
 有关更多信息，请参见[\#import 指令](../../preprocessor/hash-import-directive-cpp.md)。  
  
 下面的示例生成 C1103：  
  
```  
// C1103.cpp #import "progid:a.b.id.1.5" no_registry auto_search   // C1103  
```