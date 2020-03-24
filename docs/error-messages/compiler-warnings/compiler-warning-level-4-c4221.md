---
title: 编译器警告（等级 4）C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: fa948865685af4cbd6a865cfbf1d8546b29ab280
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161134"
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
