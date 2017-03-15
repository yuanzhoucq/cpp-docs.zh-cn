---
title: "编译器错误 C2388 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2388"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2388"
ms.assetid: 764ad2d7-cb04-425f-ba30-70989488c4a4
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C2388
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“symbol”：不能同时使用 \_\_declspec\(appdomain\) 和 \_\_declspec\(process\) 来声明一个符号。  
  
 `appdomain` 和 `process``__declspec` 修饰符不能用于相同的符号。 变量的存储空间按进程或按应用程序域存在。  
  
 有关详细信息，请参见[应用程序域](../../cpp/appdomain.md)和[过程](../../cpp/process.md)。  
  
 以下示例生成 C2388：  
  
```  
// C2388.cpp // compile with: /clr /c __declspec(process) __declspec(appdomain) int i;   // C2388 __declspec(appdomain) int i;   // OK  
```