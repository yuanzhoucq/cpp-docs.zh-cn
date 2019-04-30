---
title: 编译器警告（等级 4）C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: 11c6b1ad50c44ac4ad2a9d014e57efef097d9d8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401171"
---
# <a name="compiler-warning-level-4-c4208"></a>编译器警告（等级 4）C4208

使用了非标准扩展： delete [exp]-计算但忽略 exp

通过 Microsoft 扩展 (/Ze)，可以删除数组中使用括号内的某个值[delete 运算符](../../cpp/delete-operator-cpp.md)。 忽略的值。

```
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

此类值都无效 ANSI 兼容性 ([/Za](../../build/reference/za-ze-disable-language-extensions.md))。