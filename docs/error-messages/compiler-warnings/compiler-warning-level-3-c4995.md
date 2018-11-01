---
title: 编译器警告 （等级 3） C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: 54bc8931b5eaa3bbb5053e5c21aa2aaaa73126fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50624791"
---
# <a name="compiler-warning-level-3-c4995"></a>编译器警告 （等级 3） C4995

function： 名称被标记为不推荐使用的 #pragma

编译器遇到标记有杂注的函数[弃用](../../preprocessor/deprecated-c-cpp.md)。 在未来版本中可能不再支持此函数。 您可以关闭此警告与[警告](../../preprocessor/warning.md)杂注 （下面的示例）。

## <a name="example"></a>示例

下面的示例生成 C4995:

```
// C4995.cpp
// compile with: /W3
#include <stdio.h>

// #pragma warning(disable : 4995)
void func1(void)
{
    printf("\nIn func1");
}

int main()
{
    func1();
    #pragma deprecated(func1)
    func1();   // C4995
}
```