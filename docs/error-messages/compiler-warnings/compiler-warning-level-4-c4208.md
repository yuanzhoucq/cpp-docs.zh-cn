---
title: 编译器警告（等级 4）C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: c6e83feacd08bdb2203873a14a47ebde686a94f9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991605"
---
# <a name="compiler-warning-level-4-c4208"></a>编译器警告（等级 4）C4208

使用了非标准扩展： delete [exp]-计算但忽略 exp

使用 Microsoft 扩展（/Ze），可以使用包含[delete 运算符](../../cpp/delete-operator-cpp.md)的括号内的值删除数组。 值被忽略。

```cpp
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

此类值在 ANSI 兼容性（[/za](../../build/reference/za-ze-disable-language-extensions.md)）下无效。
