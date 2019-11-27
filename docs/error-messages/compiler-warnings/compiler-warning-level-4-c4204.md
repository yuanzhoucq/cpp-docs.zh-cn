---
title: 编译器警告（等级 4）C4204
ms.date: 11/04/2016
f1_keywords:
- C4204
helpviewer_keywords:
- C4204
ms.assetid: 298d2880-6737-448e-b711-15572d540200
ms.openlocfilehash: ecbe8bddd3f868070470555e79608ac1ecce380a
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541675"
---
# <a name="compiler-warning-level-4-c4204"></a>编译器警告（等级 4）C4204

使用了非标准扩展：非常量聚合初始值设定项

利用 Microsoft 扩展（/Ze），可以用不是常量的值初始化聚合类型（数组、结构、联合和类）。

## <a name="example"></a>示例

```c
// C4204.c
// compile with: /W4
int func1()
{
   return 0;
}
struct S1
{
   int i;
};

int main()
{
   struct S1 s1 = { func1() };   // C4204
   return s1.i;
}
```

此类初始化在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。