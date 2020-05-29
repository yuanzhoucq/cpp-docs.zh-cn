---
title: __ptr32、__ptr64
ms.date: 10/09/2018
f1_keywords:
- __ptr32_cpp
- __ptr64_cpp
- __ptr32
- __ptr64
- _ptr32
- _ptr64
helpviewer_keywords:
- __ptr64 keyword [C++]
- _ptr32 keyword [C++]
- ptr32 keyword [C++]
- ptr64 keyword [C++]
- _ptr64 keyword [C++]
- __ptr32 keyword [C++]
ms.assetid: afb563d8-7458-4fe7-9c30-bd4b5385a59f
ms.openlocfilehash: c3ebe642284c6ee269dbfc39985630b7d949435f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80179206"
---
# <a name="__ptr32-__ptr64"></a>__ptr32、__ptr64

**Microsoft 专用**

**__ptr32**表示32位系统上的本机指针，而 **__ptr64**表示64位系统上的本机指针。

以下示例演示如何声明所有这些指针类型：

```cpp
int * __ptr32 p32;
int * __ptr64 p64;
```

在32位系统上，使用 **__ptr64**声明的指针将被截断为32位指针。 在64位系统上，使用 **__ptr32**声明的指针被强制转换为64位指针。

> [!NOTE]
> 使用 **/clr： pure**进行编译时，不能使用 **__ptr32**或 **__ptr64** 。 否则，将生成编译器错误 C2472。 **/Clr： pure**和 **/clr： safe**编译器选项在 visual studio 2015 中已弃用，在 visual studio 2017 中不受支持。

为了与早期版本兼容， **_ptr32**和 **_ptr64**是 **__ptr32**和 **__ptr64**的同义词，除非指定编译器选项[/za \(禁用语言扩展）](../build/reference/za-ze-disable-language-extensions.md) 。

## <a name="example"></a>示例

下面的示例演示如何声明和分配带有 **__ptr32**和 **__ptr64**关键字的指针。

```cpp
#include <cstdlib>
#include <iostream>

int main()
{
    using namespace std;

    int * __ptr32 p32;
    int * __ptr64 p64;

    p32 = (int * __ptr32)malloc(4);
    *p32 = 32;
    cout << *p32 << endl;

    p64 = (int * __ptr64)malloc(4);
    *p64 = 64;
    cout << *p64 << endl;
}
```

```Output
32
64
```

**结束 Microsoft 专用**

## <a name="see-also"></a>另请参阅

[内置类型](../cpp/fundamental-types-cpp.md)
