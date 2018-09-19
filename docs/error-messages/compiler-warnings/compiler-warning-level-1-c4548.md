---
title: 编译器警告 （等级 1） C4548 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4548
dev_langs:
- C++
helpviewer_keywords:
- C4548
ms.assetid: 2cee817e-e463-4d90-bbd2-de120d48c101
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 19ad8863858e7bbb4fdc5f200926ef4ab93ab794
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086637"
---
# <a name="compiler-warning-level-1-c4548"></a>编译器警告（等级 1）C4548

逗号前的表达式不起任何作用；应输入带副作用的表达式

编译器检测到的格式不正确的逗号表达式。

默认情况下，此警告处于关闭状态。 有关详细信息，请参阅 [Compiler Warnings That Are Off by Default](../../preprocessor/compiler-warnings-that-are-off-by-default.md)。

下面的示例生成 C4548:

```
// C4548.cpp
// compile with: /W1
#pragma warning (default : 4548)
int main()
{
   int i = 0, k = 0;

   if ( i, k )   // C4548
   // try the following line instead
   // if ( i = 0, k )
      i++;
}
```