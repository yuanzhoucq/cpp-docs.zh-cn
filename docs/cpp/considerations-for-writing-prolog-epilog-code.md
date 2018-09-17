---
title: 有关编写 Prolog / Epilog 代码的注意事项 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- stack frame layout
- prolog code
- epilog code
- __LOCAL_SIZE constant
- stack, stack frame layout
ms.assetid: c7814de2-bb5c-4f5f-96d0-bcfd2ad3b182
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 063bbb74f0cb1b0a6396448ba7d6be7bf91dab85
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720383"
---
# <a name="considerations-for-writing-prologepilog-code"></a>有关编写 Prolog/Epilog 代码的注意事项
 **Microsoft 专用**
 
 在编写你自己的 prolog 和 epilog 代码序列之前，请务必了解堆栈帧的布局方式。它也是有助于了解如何使用`__LOCAL_SIZE`符号。  
  
##  <a name="_pluslang_c.2b2b_.stack_frame_layout"></a> 堆栈帧布局  
 此示例显示了可能出现在 32 位函数中的标准 prolog 代码：  
  
```  
push        ebp                ; Save ebp  
mov         ebp, esp           ; Set stack frame pointer  
sub         esp, localbytes    ; Allocate space for locals  
push        <registers>        ; Save registers  
```  
  
 `localbytes` 变量表示局部变量堆栈上所需的字节数，`<registers>` 变量是表示要保存在堆栈上的寄存器列表的占位符。 推入寄存器后，您可以将任何其他适当的数据放置在堆栈上。 下面是相应的 epilog 代码：  
  
```  
pop         <registers>   ; Restore registers  
mov         esp, ebp      ; Restore stack pointer  
pop         ebp           ; Restore ebp  
ret                       ; Return from function  
```  
  
 堆栈始终向下增长（从高内存地址到低内存地址）。 基指针 (`ebp`) 指向 `ebp` 的推入值。 本地区域开始于 `ebp-4`。 若要访问局部变量，可通过从 `ebp` 中减去适当的值来计算 `ebp` 的偏移量。  
  
##  <a name="_pluslang___local_size"></a> __LOCAL_SIZE  
 编译器提供了一个符号， `__LOCAL_SIZE`，用于函数 prolog 代码的内联汇编程序块。 此符号用于在自定义 prolog 代码中的堆栈帧上为局部变量分配空间。  
  
 编译器确定的值`__LOCAL_SIZE`。 其值是所有用户定义的局部变量和编译器生成的临时变量的总字节数。 `__LOCAL_SIZE` 可以仅用作即时操作数;它不能在表达式中使用。 不得更改或重新定义此符号的值。 例如：  
  
```  
mov        eax, __LOCAL_SIZE           ;Immediate operand--Okay  
mov        eax, [ebp - __LOCAL_SIZE]   ;Error  
```  
  
 序列包含自定义 prolog 和 epilog 的裸函数的以下示例使用`__LOCAL_SIZE`在 prolog 序列中的符号：  
  
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
  
**结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [Naked 函数调用](../cpp/naked-function-calls.md)