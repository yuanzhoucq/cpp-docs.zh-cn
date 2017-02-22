---
title: "编译器错误 C3556 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C3556"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3556"
ms.assetid: 9b002dcc-494e-414f-9587-20c2a0a39333
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 编译器错误 C3556
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“expression”:“decltype”的参数不正确  
  
 编译器无法推导作为 `decltype(``expression``)` 类型说明符参数的表达式的类型。 在下面的代码示例中，编译器无法推导 `myFunction` 参数的类型，因为 `myFunction` 会进行重载。  
  
```  
void myFunction(); void myFunction(int); decltype(myFunction); // C3556  
```