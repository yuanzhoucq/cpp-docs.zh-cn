---
title: 编译器警告（等级 4）C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 1b165d2bdb2fb50df89fdd77c734c054a40b6e95
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622477"
---
# <a name="compiler-warning-level-4-c4205"></a>编译器警告（等级 4）C4205

使用了非标准扩展： 函数范围内的静态函数声明

通过 Microsoft 扩展 (/Ze)**静态**可以在另一个函数内声明函数。 该函数具有全局作用域。

## <a name="example"></a>示例

```
// C4205.c
// compile with: /W4
void func1()
{
   static int func2();  // C4205
};

int main()
{
}
```

此类初始化将是无效 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。