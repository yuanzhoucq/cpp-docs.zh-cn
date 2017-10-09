---
title: "内联汇编程序 (C) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- __asm keyword [C]
- inline assembler [C]
ms.assetid: 821acc77-60b1-434c-ba54-2ba930a25ab4
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 5456b9c750a7aba33282f95097826362434e9840
ms.contentlocale: zh-cn
ms.lasthandoff: 10/09/2017

---
# <a name="inline-assembler-c"></a>内联汇编程序 (C)
**Microsoft 专用**  
  
 利用内联汇编程序，您可以直接在 C 源程序中嵌入汇编语言指令，而无需额外的程序集和链接步骤。 内联汇编程序生成到该编译器中，因此您不需要一个单独的汇编程序，例如 Microsoft Macro Assembler (MASM)。  
  
 由于内联汇编程序不需要单独的程序集和链接步骤，因此它比单独的汇编程序更方便。 内联程序集代码可以使用任何 C 变量或范围中的函数名，因此，将其与程序的 C 代码集成非常容易。 由于程序集代码可以与 C 语句混合，因此它可以完成在单独的 C 中难以完成或无法完成的任务。  
  
 `__asm` 关键字调用内联汇编程序，并且可在 C 语句合法的任何位置显示。 它不能单独出现。 它必须后跟一个程序集指令、一组括在大括号中的指令或者至少一对空大括号。 此处的术语“`__asm` 块”指任何指令或指令组（无论是否在大括号中）。  
  
 以下代码是括在大括号内的简单 `__asm` 块。 （此代码是一个自定义函数 prolog 序列。）  
  
```  
__asm  
{  
   push ebp  
   mov  ebp, esp  
   sub  esp, __LOCAL_SIZE  
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
  
## <a name="see-also"></a>另请参阅  
 [函数特性](../c-language/function-attributes.md)
