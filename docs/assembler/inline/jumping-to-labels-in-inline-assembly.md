---
title: "跳转到内联程序集中的标签 | Microsoft Docs"
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
  - "__asm 关键字 [C++], 标签"
  - "区分大小写, 内联程序集中的标签"
  - "内联程序集, 跳转到标签"
  - "跳转到内联程序集中的标签"
  - "标签, 在 __asm 块中"
  - "标签, 在内联程序集中"
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 跳转到内联程序集中的标签
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 与普通的 C 或 C\+\+ 标签一样，`__asm` 块的标签具有在整个已定义的函数中的范围（不只是在块中）。  程序集指令和 `goto` 语句可以跳转到 `__asm` 块内部或外部的标签。  
  
 `__asm` 块中定义的标签不区分大小写；`goto` 语句和程序集指令可以引用这些标签而无需考虑大小写。  C 和 C\+\+ 标签仅在由 `goto` 语句使用时区分大小写。  程序集指令可以跳转到 C 或 C\+\+ 标签而不考虑大小写。  
  
 以下代码显示了所有排列：  
  
```  
void func( void )  
{  
   goto C_Dest;  /* Legal: correct case   */  
   goto c_dest;  /* Error: incorrect case */  
  
   goto A_Dest;  /* Legal: correct case   */  
   goto a_dest;  /* Legal: incorrect case */  
  
   __asm  
   {  
      jmp C_Dest ; Legal: correct case  
      jmp c_dest ; Legal: incorrect case  
  
      jmp A_Dest ; Legal: correct case  
      jmp a_dest ; Legal: incorrect case  
  
      a_dest:    ; __asm label  
   }  
  
   C_Dest:       /* C label */   
   return;  
}  
int main()  
{  
}  
```  
  
 不要使用 C 库函数名称作为 `__asm` 块中的标签。  例如，您可能想使用 `exit` 作为标签，如下所示：  
  
```  
; BAD TECHNIQUE: using library function name as label  
jne exit  
   .  
   .  
   .  
exit:  
   ; More __asm code follows  
```  
  
 由于 **exit** 是 C 库函数的名称，因此该代码可能跳转到 **exit** 函数而非所需位置。  
  
 与在 MASM 程序中一样，美元符号 \(`$`\) 用作当前位置计数器。  它是当前组合的指令的标签。  在 `__asm` 块中，其主要用途是做长条件跳转：  
  
```  
jne $+5 ; next instruction is 5 bytes long  
jmp farlabel  
; $+5  
   .  
   .  
   .  
farlabel:  
```  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [内联汇编程序](../../assembler/inline/inline-assembler.md)