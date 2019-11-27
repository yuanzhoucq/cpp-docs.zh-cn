---
title: 编译器警告（等级3） C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: 4c31023fbcb36c53a7d0f5138c280ff12c4d495e
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541181"
---
# <a name="compiler-warning-level-3-c4995"></a>编译器警告（等级3） C4995

"function"：名称被标记为 #pragma 不推荐使用

编译器遇到了已[使用杂注](../../preprocessor/deprecated-c-cpp.md)标记的函数。 在未来版本中可能不再支持此函数。 可以通过[警告](../../preprocessor/warning.md)杂注关闭此警告（以下示例）。

## <a name="example"></a>示例

下面的示例生成 C4995：

```cpp
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