---
title: 编译器警告（等级 4）C4205
ms.date: 11/04/2016
f1_keywords:
- C4205
helpviewer_keywords:
- C4205
ms.assetid: 39b5108c-7230-41b4-b2fe-2293eb6aae28
ms.openlocfilehash: 7b6e273de196f6708b92774ce5b436dc810ad3a5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80161434"
---
# <a name="compiler-warning-level-4-c4205"></a>编译器警告（等级 4）C4205

使用了非标准扩展：函数范围内的静态函数声明

利用 Microsoft 扩展（/Ze），可以在另一个函数内声明**静态**函数。 函数被赋予全局范围。

## <a name="example"></a>示例

```c
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

此类初始化在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。
