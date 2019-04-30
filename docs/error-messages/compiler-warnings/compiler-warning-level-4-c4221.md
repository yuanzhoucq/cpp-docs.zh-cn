---
title: 编译器警告（等级 4）C4221
ms.date: 11/04/2016
f1_keywords:
- C4221
helpviewer_keywords:
- C4221
ms.assetid: 8532bd68-54dc-4526-8597-f61dcb0a0129
ms.openlocfilehash: f552a5d76d1a778cdf72cbe079138f609350ffb1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401093"
---
# <a name="compiler-warning-level-4-c4221"></a>编译器警告（等级 4）C4221

使用了非标准扩展: identifier： 不能使用自动变量的地址初始化

使用默认的 Microsoft 扩展 (/Ze) 中，您可以初始化聚合类型 (**数组**， `struct`，或**联合**) 与本地 （自动） 变量的地址。

## <a name="example"></a>示例

```
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

此类初始化将是无效 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。