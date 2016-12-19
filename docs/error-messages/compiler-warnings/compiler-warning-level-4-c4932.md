---
title: "编译器警告（等级 4）C4932 | Microsoft Docs"
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
  - "C4932"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4932"
ms.assetid: 0b8d88cc-21f6-45cb-a9f5-1795b7db0dfa
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 4）C4932
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\_\_identifier\(identifier\)和 \_\_identifier\(identifier\)无法区分  
  
 编译器无法区分作为参数传递到 [\_\_identifier](../../windows/identifier-cpp-cli.md) 的 **\_finally** 与 `__finally` 或 `__try` 与 **\_try**。 不要尝试在同一程序中将它们同时用作标识符，因为这将导致 [C2374](../../error-messages/compiler-errors-1/compiler-error-c2374.md) 错误。  
  
 下面的示例生成 C4932：  
  
```  
// C4932.cpp // compile with: /clr /W4 /WX int main() { int __identifier(_finally) = 245;   // C4932 int __identifier(__finally) = 25;   // C4932 }  
```