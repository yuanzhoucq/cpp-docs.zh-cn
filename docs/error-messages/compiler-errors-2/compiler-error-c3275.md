---
title: "编译器错误 C3275 | Microsoft Docs"
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
  - "C3275"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3275"
ms.assetid: 5752680f-7d3e-4c42-ba9c-845e09d32e7a
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3275
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“enum member”：无法使用该无限定符的符号  
  
 使用托管代码以及两个或多个枚举包含具有相同名称的标识符时，必须显式限定对标识符的引用。  
  
 只能使用 **\/clr:oldSyntax** 访问 C3275。  
  
 下面的示例演示了可能生成 C3275 的两种情况：  
  
```  
// C3275.cpp // compile with: /clr:oldSyntax #using <mscorlib.dll> __value enum Jewelry { necklace, brooch, pin, ring, earring }; __value enum Phone { busy, ring, disconnect }; int main() { Phone p = ring;   // C3275 // try the following line instead // Phone p = Phone::ring; Console::Out->Write(ring);   // C3275 // try the following line instead // Console::Out->Write(Phone::ring); }  
```