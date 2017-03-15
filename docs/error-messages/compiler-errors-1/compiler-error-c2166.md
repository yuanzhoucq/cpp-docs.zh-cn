---
title: "编译器错误 C2166 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2166"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2166"
ms.assetid: 12789c3a-cc76-48bb-ae2e-64283e0964ed
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 编译器错误 C2166
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

左值指定 const 对象  
  
 代码尝试修改声明为 `const` 的项。  
  
 下面的示例生成 C2166：  
  
```  
// C2166.cpp int f(); int main() { ( (const int&) 1 ) = 5;   // C2166 }  
```