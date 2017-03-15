---
title: "使用内联程序集编写函数 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 关键字 [C++], 在函数中"
  - "汇编程序 [C++], 写入函数"
  - "函数 [C++], 内联程序集"
  - "内联程序集 [C++], 写入函数"
ms.assetid: b5df8a04-fdc7-4622-8c9e-e4b618927497
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 使用内联程序集编写函数
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 如果您编写一个函数的内联程序集代码，可以很容易地传递给函数的参数和返回值从它。  下面的示例将第一次为单独的程序集，然后重新编写为内联汇编函数进行比较。  调用的函数 `power2`，接收两个参数，第一个参数乘以 2 的幂的第二个参数。  编写的单独的程序集，该函数可能如下所示：  
  
```  
; POWER.ASM  
; Compute the power of an integer  
;  
       PUBLIC _power2  
_TEXT SEGMENT WORD PUBLIC 'CODE'  
_power2 PROC  
  
        push ebp        ; Save EBP  
        mov ebp, esp    ; Move ESP into EBP so we can refer  
                        ;   to arguments on the stack  
        mov eax, [ebp+4] ; Get first argument  
        mov ecx, [ebp+6] ; Get second argument  
        shl eax, cl     ; EAX = EAX * ( 2 ^ CL )  
        pop ebp         ; Restore EBP  
        ret             ; Return with sum in EAX  
  
_power2 ENDP  
_TEXT   ENDS  
        END  
```  
  
 它专为单独的程序集，因为函数需要单独的源代码文件和程序集以及链接步骤。  通常 C 和 c \+ \+ 函数参数传递到堆栈上，所以此版本的`power2`函数访问通过它们在堆栈上的位置及其参数。  （请注意， **模型**指令，可用在 MASM 和某些其他组装器，还可以按名称访问堆栈参数和本地堆栈变量。）  
  
## 示例  
 此程序将写入`power2`函数的内联程序集代码：  
  
```  
// Power2_inline_asm.c  
// compile with: /EHsc  
// processor: x86  
  
#include <stdio.h>  
  
int power2( int num, int power );  
  
int main( void )  
{  
    printf_s( "3 times 2 to the power of 5 is %d\n", \  
              power2( 3, 5) );  
}  
int power2( int num, int power )  
{  
   __asm  
   {  
      mov eax, num    ; Get first argument  
      mov ecx, power  ; Get second argument  
      shl eax, cl     ; EAX = EAX * ( 2 to the power of CL )  
   }  
   // Return with result in EAX  
}  
```  
  
 内联版本的`power2`函数按名称引用它的参数，并显示在与该程序的其余部分相同的源文件。  此版本还需要较少的程序集指令。  
  
 因为内联版本的`power2`不执行 C  `return`语句，它可以导致无害的警告，如果在编译时警告级别 2 或更高版本。  函数返回一个值，但编译器无法区分，没有`return`语句。  您可以使用 [\#pragma 警告](../../preprocessor/warning.md)若要禁用此警告的生成。  
  
 **最终 Microsoft 特定**  
  
## 请参阅  
 [在 \_\_asm 块中使用 C 或 C\+\+](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)