---
title: 编译器警告（等级 4）C4703
ms.date: 11/04/2016
f1_keywords:
- C4703
helpviewer_keywords:
- C4703
ms.assetid: 5dad454e-69e3-4931-9168-050a861c05f8
ms.openlocfilehash: 5033490550f318cab65f984cab81b08102641c9d
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518356"
---
# <a name="compiler-warning-level-4-c4703"></a>编译器警告（等级 4）C4703

使用了可能未初始化的局部指针变量“name”

本地指针变量*名称*可能已被使用，但没有赋予值。 这可能导致不可预知的结果。

## <a name="example"></a>示例

以下代码生成了 C4701 和 C4703。

```cpp
#include <malloc.h>

void func(int size)
{
    void* p;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr) // C4701 and C4703
        free(p);
}

int main()
{
    func(9);
}
```

```Output
c:\src\test.cpp(10) : warning C4701: potentially uninitialized local variable 'p' used
c:\src\test.cpp(10) : warning C4703: potentially uninitialized local pointer variable 'p' used
```

若要更正此警告，请初始化该变量，如以下示例所示：

```cpp
#include <malloc.h>

void func(int size)
{
    void* p = nullptr;
    if (size < 256) {
        p = malloc(size);
    }

    if (p != nullptr)
        free(p);
}

int main()
{
    func(9);
}
```

## <a name="see-also"></a>另请参阅

[编译器警告（等级 4）C4701](../../error-messages/compiler-warnings/compiler-warning-level-4-c4701.md)<br/>
[警告、/sdl 和改进未初始化的变量检测](https://www.microsoft.com/security/blog/2012/06/06/warnings-sdl-and-improving-uninitialized-variable-detection/)
