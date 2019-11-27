---
title: 编译器警告（等级 4）C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: fa87c240472df2926753781f0f14cbd69752de00
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541930"
---
# <a name="compiler-warning-level-4-c4221"></a>编译器警告（等级 4）C4221

使用了非标准扩展： "identifier"：无法使用自动变量的地址初始化

使用默认的 Microsoft 扩展（/Ze），您可以使用本地（自动）变量的地址初始化聚合类型（**数组**、`struct`或**联合**）。

## <a name="example"></a>示例

```c
// C4221.c
// compile with: /W4
struct S
{
   int *i;
};

void func()
{
   int j;
   struct S s1 = { &j };   // C4221
}

int main()
{
}
```

此类初始化在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。