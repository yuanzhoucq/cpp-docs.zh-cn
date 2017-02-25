---
title: "编译器警告（等级 1）C4160 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4160"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4160"
ms.assetid: a9610cb7-cac4-4a74-8b4e-049030ebb92b
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# 编译器警告（等级 1）C4160
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**\#pragma**   
 ***pragma* \(pop,...\)：未找到先前入栈的标识符“**   
 ***identifier* '**  
  
 源代码中的 pragma 语句试图弹出尚未入栈的标识符。 要避免此警告，请确保要弹出的标识符已正确入栈。  
  
 下面的示例生成 C4160：  
  
```  
// C4160.cpp // compile with: /W1 #pragma pack(push) #pragma pack(pop, id)   // C4160 // use identifier when pushing to resolve the warning // #pragma pack(push, id) int main() { }  
```