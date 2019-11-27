---
title: 编译器警告（等级 4）C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: e15140bd2f0983bde64c89a054fd733d1ab902ac
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541870"
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