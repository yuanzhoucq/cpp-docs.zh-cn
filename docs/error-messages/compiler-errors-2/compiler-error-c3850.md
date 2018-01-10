---
title: "编译器错误 C3850 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3850
dev_langs: C++
helpviewer_keywords: C3850
ms.assetid: 028f3a37-f3ad-4ebc-9168-3cdea47524d4
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fe77bb54a72c340a2fbf2a986a4346397cff11fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3850"></a>编译器错误 C3850
“char”：通用字符名称指定的字符无效  
  
 表示为通用字符名称的字符必须表示 0-10FFFF 范围内的有效 Unicode 码位。 通用字符名称不能包含 Unicode 代理项范围、D800-DFFF 或编码的代理项对中的值。 编译器从有效码位自动生成代理项对。  
  
 在编译为 C 语言的代码中，通用字符名称不能表示 0000-009F（含）范围内的字符，024（“$”）、0040（“@”）和 0060（“`”）除外。  
  
 在编译为 C++ 的代码中，通用字符名称可以使用字符串或字符文本中的任意有效 Unicode 码位。 在文字之外，通用字符名称不能表示 0000-001F 或 007F-009F（均含）范围内的控制字符或基本源字符集成员。  有关详细信息，请参阅 [Character Sets](../../cpp/character-sets2.md)。  
  
## <a name="example"></a>示例  
 下面的示例生成 C3850，并演示如何修复此错误：  
  
```cpp  
// C3850.cpp  
int main() {  
   int \u0019 = 0;   // C3850, not in allowed range for an identifier  
   const wchar_t * wstr_bad  = L"\UD840DC8A"; // C3850, UCN is surrogate pair  
   const wchar_t * wstr_good = L"\U0002008A"; // Okay, UCN is valid code point  
}  
```