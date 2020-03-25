---
title: 编译器警告（等级 1）C4733
ms.date: 11/04/2016
f1_keywords:
- C4733
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
ms.openlocfilehash: 39674c32deb506725aa5f7c1f5f875e771519938
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185667"
---
# <a name="compiler-warning-level-1-c4733"></a>编译器警告（等级 1）C4733

内联 asm 分配到 "FS： 0"：处理程序未注册为安全处理程序

用于修改 FS 的值的函数：0若要添加新的异常处理程序，可能不会使用安全异常，因为该处理程序可能不会注册为有效的异常处理程序（请参阅[/SAFESEH](../../build/reference/safeseh-image-has-safe-exception-handlers.md)）。

若要解决此警告，请删除 FS：0定义或关闭此警告并使用[。](../../assembler/masm/dot-safeseh.md)用于指定安全异常处理程序的 SAFESEH。

下面的示例生成 C4733：

```cpp
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
