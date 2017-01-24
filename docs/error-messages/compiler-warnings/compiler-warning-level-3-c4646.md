---
title: "编译器警告（等级 3）C4646 | Microsoft Docs"
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
  - "C4646"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4646"
ms.assetid: 23677e8e-603e-40e0-b99a-2e4894a1278e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器警告（等级 3）C4646
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

用 \_\_declspec\(noreturn\) 声明的函数有非 void 返回类型  
  
 标记有 [noreturn](../../cpp/noreturn.md) `__declspec` 修饰符的函数应有 [void](../../cpp/void-cpp.md) 返回类型。  
  
 下面的示例生成 C4646：  
  
```  
// C4646.cpp // compile with: /W3 /WX int __declspec(noreturn) TestFunction() {   // C4646  make return type void }  
```