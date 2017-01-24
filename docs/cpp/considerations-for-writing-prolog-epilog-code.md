---
title: "编写 Prolog/Epilog 代码的注意事项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__LOCAL_SIZE 常量"
  - "epilog 代码"
  - "prolog 代码"
  - "堆栈帧布局"
  - "堆栈, 堆栈帧布局"
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 编写 Prolog/Epilog 代码的注意事项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 在编写您自己的 prolog 和 epilog 代码序列之前，请务必了解堆栈帧的布局方式。  了解如何使用 **\_\_LOCAL\_SIZE** 符号也很有用。  
  
##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a> 堆栈帧布局  
 此示例显示了可能出现在 32 位函数中的标准 prolog 代码：  
  
```  
push        ebp                ; Save ebp  
mov         ebp, esp           ; Set stack frame pointer  
sub         esp, localbytes    ; Allocate space for locals  
push        <registers>        ; Save registers  
```  
  
 `localbytes` 变量表示局部变量堆栈上所需的字节数，`<registers>` 变量是表示要保存在堆栈上的寄存器列表的占位符。  推入寄存器后，您可以将任何其他适当的数据放置在堆栈上。  下面是相应的 epilog 代码：  
  
```  
pop         <registers>   ; Restore registers  
mov         esp, ebp      ; Restore stack pointer  
pop         ebp           ; Restore ebp  
ret                       ; Return from function  
```  
  
 堆栈始终向下增长（从高内存地址到低内存地址）。  基指针 \(`ebp`\) 指向 `ebp` 的推入值。  本地区域开始于 `ebp-4`。  若要访问局部变量，可通过从 `ebp` 中减去适当的值来计算 `ebp` 的偏移量。  
  
##  <a name="_pluslang___local_size"></a> \_\_LOCAL\_SIZE  
 编译器提供符号 **\_\_LOCAL\_SIZE** 以用于函数 prolog 代码的内联汇编程序块中。  此符号用于在自定义 prolog 代码中的堆栈帧上为局部变量分配空间。  
  
 编译器确定 **\_\_LOCAL\_SIZE** 的值。  其值是所有用户定义的局部变量和编译器生成的临时变量的总字节数。  **\_\_LOCAL\_SIZE** 只能用作即时操作数；它不能在表达式中使用。  不得更改或重新定义此符号的值。  例如：  
  
```  
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov        eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 以下包含自定义 prolog 和 epilog 序列的裸函数的示例在 prolog 序列中使用 **\_\_LOCAL\_SIZE** 符号：  
  
```  
// the__local_size_symbol.cpp  
// processor: x86  
__declspec ( naked ) int main() {  
   int i;  
   int j;  
  
   __asm {      /* prolog */  
      push   ebp  
      mov      ebp, esp  
      sub      esp, __LOCAL_SIZE  
      }  
  
   /* Function body */  
   __asm {   /* epilog */  
      mov      esp, ebp  
      pop      ebp  
      ret  
      }  
}  
```  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [Naked 函数调用](../cpp/naked-function-calls.md)