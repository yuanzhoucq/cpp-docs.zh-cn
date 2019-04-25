---
title: 在内联汇编程序内跳转到标签
ms.date: 08/30/2018
helpviewer_keywords:
- inline assembly, jumping to labels
- labels, in inline assembly
- __asm keyword [C++], labels
- case sensitivity, labels in inline assembly
- labels, in __asm blocks
- jumping to labels in inline assembly
ms.assetid: 36c18b97-8981-4631-9dfd-af6c14a04297
ms.openlocfilehash: 7653dc990e2f4b490bcbe333ed6f7586ac966d2e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166901"
---
# <a name="jumping-to-labels-in-inline-assembly"></a>在内联汇编程序内跳转到标签

**Microsoft 专用**

与普通的 C 或 C++ 标签一样，`__asm` 块的标签具有在整个已定义的函数中的范围（不只是在块中）。 程序集指令和 `goto` 语句可以跳转到 `__asm` 块内部或外部的标签。

`__asm` 块中定义的标签不区分大小写；`goto` 语句和程序集指令可以引用这些标签而无需考虑大小写。 C 和 C++ 标签仅在由 `goto` 语句使用时区分大小写。 程序集指令可以跳转到 C 或 C++ 标签而不考虑大小写。

以下代码显示了所有排列：

```cpp
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

不要使用 C 库函数名称作为 `__asm` 块中的标签。 例如，您可能想使用 `exit` 作为标签，如下所示：

```cpp
; BAD TECHNIQUE: using library function name as label
   jne exit
   .
   .
   .
exit:
   ; More __asm code follows
```

因为**退出**名称的 C 库函数，该代码可能跳转到**退出**函数而不是到所需位置。

与在 MASM 程序中一样，美元符号 (`$`) 用作当前位置计数器。 它是当前组合的指令的标签。 在 `__asm` 块中，其主要用途是做长条件跳转：

```cpp
   jne $+5 ; next instruction is 5 bytes long
   jmp farlabel ; $+5
   .
   .
   .
farlabel:
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>