---
title: 编译器警告（等级 4）C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: 0d5e7dd45b58f1231c39565bfd74c5895096a8b7
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541647"
---
# <a name="compiler-warning-level-4-c4202"></a>编译器警告（等级 4）C4202

使用了非标准扩展： "..."：名称列表中的原型参数非法

旧式函数定义包含变量参数。 这些定义在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下生成错误。

## <a name="example"></a>示例

```c
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```