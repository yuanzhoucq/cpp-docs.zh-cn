---
title: "编译器错误 C2469 | Microsoft Docs"
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
  - "C2469"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2469"
ms.assetid: 3814bdff-581a-4d3e-8b47-8de6887cea69
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C2469
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“operator”: 无法分配“type”对象  
  
 向运算符传递了一个无效类型。  
  
 下面的示例生成 C2469：  
  
```  
// C2469.cpp int main() { int *i = new void;   // C2469 int *i = new int;   // OK }  
```