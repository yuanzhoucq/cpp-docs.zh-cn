---
title: 编译器警告（等级 4）C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: e925f315e8506453403b0a0eda75b7c2956cc05c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219932"
---
# <a name="compiler-warning-level-4-c4221"></a>编译器警告（等级 4）C4221

使用了非标准扩展： "identifier"：无法使用自动变量的地址初始化

使用默认的 Microsoft 扩展（/Ze），您可以**array** **`struct`** **`union`** 使用本地（自动）变量的地址初始化聚合类型（数组、或）。

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
