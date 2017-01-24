---
title: "编译器错误 C3850 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3850"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3850"
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 编译器错误 C3850
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“char”：通用字符名称指定的字符无效  
  
 表示为通用字符名称的字符必须表示 0\-10FFFF 范围内的有效 Unicode 码位。 通用字符名称不能包含 Unicode 代理项范围、D800\-DFFF 或编码的代理项对中的值。 编译器从有效码位自动生成代理项对。  
  
 在编译为 C 语言的代码中，通用字符名称不能表示 0000\-009F（含）范围内的字符，024（“$”）、0040（“@”）和 0060（“\`”）除外。  
  
 在编译为 C\+\+ 的代码中，通用字符名称可以使用字符串或字符文本中的任意有效 Unicode 码位。 在文字之外，通用字符名称不能表示 0000\-001F 或 007F\-009F（均含）范围内的控制字符或基本源字符集成员。  有关详细信息，请参阅 [字符集](../../cpp/character-sets2.md)。  
  
## 示例  
 下面的示例生成 C3850，并演示如何修复此错误：  
  
```cpp  
// C3850.cpp int main() { int \u0019 = 0;   // C3850, not in allowed range for an identifier const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point }  
```