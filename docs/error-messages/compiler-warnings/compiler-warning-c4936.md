---
title: "编译器警告 C4936 | Microsoft Docs"
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
  - "C4936"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4936"
ms.assetid: 6676de35-bf1b-4d0b-a70f-b5734130336c
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告 C4936
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

只有使用 \/clr 或 \/clr:pure 编译时，才支持此 \_\_declspec  
  
 使用了 `__declspec` 修饰符，但只有在编译时使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 选项之一的情况下 `__declspec` 修饰符方才有效。  
  
 有关详细信息，请参见[应用程序域](../../cpp/appdomain.md)和[过程](../../cpp/process.md)。  
  
 始终发出 C4936 错误。  可以使用 [警告](../../preprocessor/warning.md) 杂注来禁用 C4936。  
  
 下面的示例生成 C4936：  
  
```  
// C4936.cpp // compile with: /c // #pragma warning (disable : 4936) __declspec(process) int i;   // C4936 __declspec(appdomain) int j;   // C4936  
```