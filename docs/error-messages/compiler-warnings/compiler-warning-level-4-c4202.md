---
title: 编译器警告 （等级 C4202 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4202
dev_langs:
- C++
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4fd44b436369e908d471ff56d193f3afab97a769
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46103303"
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