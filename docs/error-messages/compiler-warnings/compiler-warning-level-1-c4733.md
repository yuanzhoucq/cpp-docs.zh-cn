---
title: 编译器警告（等级 1）C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 0d0b0b912ef15294f9a4362a79dffd6d7eeabed8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50474914"
---
# <a name="compiler-warning-level-1-c4733"></a>编译器警告（等级 1）C4733

内联 asm 分配到"fs: 0": 未注册为安全处理程序的处理程序

安全异常，因为该处理程序可能未注册为有效的异常处理程序可能无法在修改 fs: 0 若要添加新的异常处理程序处的值的函数 (请参阅[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md))。

若要解决此警告，请删除 fs: 0 定义或关闭此警告，然后使用[。SAFESEH](../../assembler/masm/dot-safeseh.md)指定安全异常处理程序。

下面的示例生成 C4733:

```
// C4733.cpp
// compile with: /W1 /c
// processor: x86
#include "stdlib.h"
#include "stdio.h"
void my_handler()
{
   printf("Hello from my_handler\n");
   exit(1);
}

int main()
{
   _asm {
      push    my_handler
      mov     eax, DWORD PTR fs:0
      push    eax
      mov     DWORD PTR fs:0, esp   // C4733
   }

   *(int*)0 = 0;
}
```