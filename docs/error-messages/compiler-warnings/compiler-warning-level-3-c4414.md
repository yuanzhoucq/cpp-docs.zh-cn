---
title: 编译器警告 （等级 3） C4414 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4414
dev_langs:
- C++
helpviewer_keywords:
- C4414
ms.assetid: bc81d3ad-55dc-4a6b-a6f2-ec0ef38347df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fd0868fea89cd868178956c0aba171ce6525bd75
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043204"
---
# <a name="compiler-warning-level-3-c4414"></a>编译器警告（等级 3）C4414

function： 短跳转到函数转换为附近

短跳转生成 compact 指令从指令分支到限制范围之内的地址。 该指令包括表示该跳转的目标地址、 函数定义之间的距离的短偏移量。 在链接过程中一个函数可能会导致函数从短的偏移量超出了可访问范围要移动的已移动或受链接时间优化。 编译器必须生成跳转，这要求为近或远的 jmp 指令的特殊记录。 编译器进行转换。

例如，下面的代码生成 C4414:

```
// C4414.cpp
// compile with: /W3 /c
// processor: x86
int DoParityEven();
int DoParityOdd();
unsigned char global;
int __declspec(naked) DoParityEither()
{
   __asm
   {
      test global,0
      jpe SHORT DoParityEven  // C4414
      jmp SHORT DoParityOdd   // C4414
   }
}
```