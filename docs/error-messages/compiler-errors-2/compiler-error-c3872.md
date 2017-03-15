---
title: "编译器错误 C3872 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3872"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3872"
ms.assetid: 519e95be-5641-40cc-894c-da4819506604
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# 编译器错误 C3872
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“char”：此字符不允许在标识符中使用  
  
 C\+\+ 编译器对于标识符中允许的字符遵循 C\+\+ 11 标准。 仅允许在标识符中使用某些范围的字符和通用字符名称。 其他限制适用于标识符的初始字符。 有关允许的字符和通用字符名称范围的详细信息和列表，请参阅[C\+\+ 标识符](../../cpp/identifiers-cpp.md)。  
  
 编译 C\+\+\/CLI 代码时，标识符中允许的字符范围限制更少。 使用 \/clr 编译的代码中的标识符应遵循[标准 ECMA\-335：公共语言基础结构 \(CLI\)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)。  
  
 下面的示例生成 C3872：  
  
```  
// C3872.cpp int main() { int abc_\u0040;   // C3872, U+0040 is in base char set int abc_\u3001;   // C3872, U+3001 is not in allowed range int \u30A2_abc_\u3042;   // OK, UCNs in allowed range }  
```