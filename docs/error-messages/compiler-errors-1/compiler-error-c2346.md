---
title: "编译器错误 C2346 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2346"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2346"
ms.assetid: 246145be-5645-4cd6-867c-e3bc39e33dca
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# 编译器错误 C2346
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

“function”不能编译为本机函数: 原因  
  
 编译器无法将函数编译为 MSIL。  
  
 有关更多信息，请参见[managed、unmanaged](../../preprocessor/managed-unmanaged.md)和[\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md)。  
  
### 更正此错误  
  
1.  移除不能编译为 MSIL 的函数中的代码。  
  
2.  请不要用 **\/clr** 编译模块，或者可以用非托管杂注将函数标记为非托管函数。  
  
## 示例  
 下面的示例生成 C2346。  
  
```  
// C2346.cpp  
// processor: x86  
// compile with: /clr   
// C2346 expected  
struct S  
{  
   S()  
   {  
      { __asm { nop } }  
   }  
   virtual __clrcall ~S() { }  
};  
  
void main()  
{  
   S s;  
}  
```