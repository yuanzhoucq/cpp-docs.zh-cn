---
title: "编译器错误 C3150 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3150"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3150"
ms.assetid: c1ff28f5-52fe-4fd4-81d0-2e0ad8548631
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3150
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“element”:“attribute”只能应用于类、接口、数组或指针  
  
 [\_\_gc](../../misc/gc.md) 只能用于类、接口或数组。  
  
 只有使用 **\/clr:oldSyntax** 才可能出现 C3150 错误。  
  
 下面的示例生成 C3150：  
  
```  
// C3150.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__gc void f()   // C3150; function cannot be managed  
{  
}  
```