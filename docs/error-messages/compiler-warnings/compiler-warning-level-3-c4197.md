---
title: 编译器警告 （等级 3） C4197 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4197
dev_langs:
- C++
helpviewer_keywords:
- C4197
ms.assetid: f766feef-82b0-4d81-8a65-33628c7db196
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e3651a305b8654b9d7d36238885233b8e583f27
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043607"
---
# <a name="compiler-warning-level-3-c4197"></a>编译器警告 （等级 3） C4197

type： 忽略强制转换中的顶级 volatile 变量

编译器检测到强制转换为右值类型用限定[易失性](../../cpp/volatile-cpp.md)，或强制转换为易失性使用限定某些类型的右值类型。 根据 C 标准 (6.5.3)，与限定的类型相关联的属性是仅对左值表达式有意义。

下面的示例生成 C4197:

```
// C4197.cpp
// compile with: /W3
#include <stdio.h>
#include <signal.h>
#include <stdlib.h>

void sigproc(int);
struct S
{
   int i;
} s;

int main()
{
   signal(SIGINT, sigproc);
   s.i = 1;
   S *pS = &s;
   for ( ; (volatile int)pS->i ; )   // C4197
      break;
   // for ( ; *(volatile int *)&pS->i ; )   // OK
   //    break;
}

void sigproc(int) // ctrl-C
{
   signal(SIGINT, sigproc);
   s.i = 0;
}

```