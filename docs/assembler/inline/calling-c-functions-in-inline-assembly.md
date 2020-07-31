---
title: 在内联汇编程序内调用 C 函数
ms.date: 08/30/2018
helpviewer_keywords:
- function calls, C functions
- function calls, in inline assembly
- functions [C], calling in inline assembly
- Visual C, functions
- inline assembly, calling functions
- __asm keyword [C++], calling functions
ms.assetid: f8a8d568-d175-4e23-9b24-36ef60a4cab3
ms.openlocfilehash: 73be1142747dc608d683e6bd847639b9df718a13
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87192621"
---
# <a name="calling-c-functions-in-inline-assembly"></a>在内联汇编程序内调用 C 函数

**Microsoft 专用**

**`__asm`** 块可以调用 c 函数，包括 c 库例程。 以下示例调用 `printf` 库例程：

```cpp
// InlineAssembler_Calling_C_Functions_in_Inline_Assembly.cpp
// processor: x86
#include <stdio.h>

char format[] = "%s %s\n";
char hello[] = "Hello";
char world[] = "world";
int main( void )
{
   __asm
   {
      mov  eax, offset world
      push eax
      mov  eax, offset hello
      push eax
      mov  eax, offset format
      push eax
      call printf
      //clean up the stack so that main can exit cleanly
      //use the unused register ebx to do the cleanup
      pop  ebx
      pop  ebx
      pop  ebx
   }
}
```

由于函数自变量在堆栈上传递，因此仅需在调用函数之前推入所需自变量（前面示例中的字符串指针）。 自变量以相反顺序被推动，因此可按所需顺序结束堆栈。 模拟 C 语句

```cpp
printf( format, hello, world );
```

此示例按照该顺序推送指向 `world`、`hello` 和 `format` 的指针，然后调用 `printf`。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[内联汇编程序](../../assembler/inline/inline-assembler.md)<br/>
