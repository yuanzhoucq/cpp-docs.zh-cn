---
title: 编译器警告 （等级 C4032
ms.date: 11/04/2016
f1_keywords:
- C4032
helpviewer_keywords:
- C4032
ms.assetid: 70dd0c85-0239-43f9-bb06-507f6a57d206
ms.openlocfilehash: fa1602d63ed9822725fea8e1b842929f221d3926
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657296"
---
# <a name="compiler-warning-level-4-c4032"></a>编译器警告 （等级 C4032

形式参数 number 具有不同的类型提升时

参数类型不兼容，通过默认提升，与以前的声明中的类型。

这是 ANSI C 中的错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md)) 和 Microsoft 扩展 (/Ze) 下的一条警告。

## <a name="example"></a>示例

```
// C4032.c
// compile with: /W4
void func();
void func(char);   // C4032, char promotes to int

int main()
{
}
```