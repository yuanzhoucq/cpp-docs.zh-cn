---
title: 编译器警告（等级 4）C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: c66e2243ee5eca55105de27c9824ee8ced338500
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536145"
---
# <a name="compiler-warning-level-4-c4202"></a>编译器警告（等级 4）C4202

使用了非标准扩展:...： 非法的名称列表中的原型参数

旧式函数定义中包含变量参数。 这些定义生成 ANSI 兼容性错误 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。

## <a name="example"></a>示例

```
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```