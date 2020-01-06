---
title: 编译器警告（等级3） C4995
ms.date: 11/04/2016
f1_keywords:
- C4995
helpviewer_keywords:
- C4995
ms.assetid: c6b61755-4730-4947-ad4d-d1c2bc82585a
ms.openlocfilehash: c361563c2272da002a0edc185cc924c64f6b5e5c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991663"
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
