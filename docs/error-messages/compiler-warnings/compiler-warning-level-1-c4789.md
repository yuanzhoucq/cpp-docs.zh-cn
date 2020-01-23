---
title: 编译器警告（等级 1）C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36278615631d017db1d1c2fc4eecf8c1612892de
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518395"
---
# <a name="compiler-warning-level-1-c4789"></a>编译器警告（等级 1）C4789

> 大小为*N*字节的缓冲区 "*identifier*" 将溢出;*M*字节将在偏移*L*开始写入

## <a name="remarks"></a>备注

当使用特定 C 运行时（CRT）函数时， **C4789**会发出缓冲区溢出警告。 它还可以在传递参数或进行赋值时报告大小不匹配。 如果数据大小在编译时是已知的，则可能出现此警告。 此警告针对那些可能会避开典型数据大小不匹配检测的情况。

将数据复制到已知在编译时太小的数据块时， **C4789**会发出警告。

如果副本使用以下 CRT 函数之一的内部形式，则会出现此警告：

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)、 [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

将参数强制转换为较大的数据类型，然后从左值引用进行复制分配时，也会出现该警告。

对于C++从不执行的代码路径，视觉对象可能会生成此警告。 可以使用 `#pragma` 临时禁用该警告，如此示例中所示：

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

这种用法使C++视觉对象不会为特定代码块生成警告。 `#pragma warning(push)` 会在 `#pragma warning(disable: 4789)` 更改现有状态之前保留该状态。 `#pragma warning(pop)` 会还原压入的状态，并移除 `#pragma warning(disable:4789)` 的效果。 有关C++预处理器指令 `#pragma`的详细信息，请参阅[警告](../../preprocessor/warning.md)和[杂注指令和 __Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

## <a name="example"></a>示例

以下示例生成 C4789。

```cpp
// C4789.cpp
// compile with: /Oi /W1 /c
#include <string.h>
#include <stdio.h>

int main()
{
    char a[20];
    strcpy(a, "0000000000000000000000000\n");   // C4789

    char buf2[20];
    memset(buf2, 'a', 21);   // C4789

    char c;
    wchar_t w = 0;
    memcpy(&c, &w, sizeof(wchar_t));
}
```

## <a name="example"></a>示例

以下示例也生成 C4789。

```cpp
// C4789b.cpp
// compile with: /W1 /O2 /c
// processor: x86
short G;

int main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```
