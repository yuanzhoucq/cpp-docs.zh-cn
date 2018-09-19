---
title: 编译器警告 （等级等级 1)c4733 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4733
dev_langs:
- C++
helpviewer_keywords:
- C4733
ms.assetid: 7ef4f577-772d-4b66-a7bf-8958a6b250bc
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75b4aac2d71267b4ba012384fe83f167f44ec2d2
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46092929"
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