---
title: 内联汇编程序概述 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-masm
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline assembler
- __asm keyword [C++], invoking inline assembler
- invoking inline assembler
- inline assembly, inline assembler
ms.assetid: d990331a-0e33-4760-8d7a-b720b0288335
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 31b0497f2fdc319115018a05618d3a16607dbef1
ms.sourcegitcommit: dbca5fdd47249727df7dca77de5b20da57d0f544
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2018
---
# <a name="inline-assembler-overview"></a>内联汇编概述
**Microsoft 专用**  
  
 利用内联汇编程序，您可以直接在 C 和 C++ 源程序中嵌入汇编语言指令，而无需执行额外的汇编和链接步骤。 内联汇编程序生成到该编译器中，因此您不需要一个单独的汇编程序，例如 Microsoft Macro Assembler (MASM)。  
  
 由于内联汇编程序不需要单独的程序集和链接步骤，因此它比单独的汇编程序更方便。 内联汇编代码可以使用范围中的任何 C 或 C++ 变量或函数名称，因此，将其与程序的 C 和 C++ 代码结合非常容易。 由于汇编代码可以与 C 和 C++ 语句结合，因此它可以完成单独用 C 或 C++ 难以完成或无法完成的任务。  
  
 [__Asm](../../assembler/inline/asm.md)关键字调用内联汇编程序，并且可以出现在 C 或 c + + 语句是合法的任何位置。 它不能单独出现。 它必须后跟一个程序集指令、一组括在大括号中的指令或者至少一对空大括号。 此处的术语“`__asm` 块”指任何指令或指令组（无论是否在大括号中）。  
  
 以下代码是括在大括号中的简单 `__asm` 块。 （此代码是一个自定义函数 prolog 序列。）  
  
```  
// asm_overview.cpp  
// processor: x86  
void __declspec(naked) main()  
{  
    // Naked functions must provide their own prolog...  
    __asm {  
        push ebp  
        mov ebp, esp  
        sub esp, __LOCAL_SIZE  
    }  
  
    // ... and epilog  
    __asm {  
        pop ebp  
        ret  
    }  
}  
```  
  
 或者，您还可以将 `__asm` 放在每个程序集指令前面：  
  
```  
__asm push ebp  
__asm mov  ebp, esp  
__asm sub  esp, __LOCAL_SIZE  
```  
  
 虽然 `__asm` 关键字是语句分隔符，但您也可将程序集说明置于相同的行上：  
  
```  
__asm push ebp   __asm mov  ebp, esp   __asm sub  esp, __LOCAL_SIZE  
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)