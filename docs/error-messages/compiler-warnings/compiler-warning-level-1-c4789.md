---
title: 编译器警告（等级 1）C4789
ms.date: 03/25/2019
f1_keywords:
- C4789
helpviewer_keywords:
- C4789
ms.assetid: 5800c301-5afb-4af0-85c1-ceb54d775234
ms.openlocfilehash: 36a5032098c5caabb1b050833e487fd58679a782
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187226"
---
# <a name="compiler-warning-level-1-c4789"></a>编译器警告（等级 1）C4789

> 缓冲区 '*标识符*的大小*N*字节将溢出;*M*将偏移量开始写入字节*L*

## <a name="remarks"></a>备注

**C4789**当使用特定 C 运行时 (CRT) 函数时缓冲区溢出警告。 传递的参数或进行分配时，它还可以报告大小不匹配。 如果在编译时已知的数据大小可能该警告。 此警告针对那些可能会避开典型数据大小不匹配检测的情况。

**C4789**会发出警告时数据将复制到具有已知要在编译时太小的数据块。

如果该副本将使用这些 CRT 函数之一的内部形式将出现警告：

- [strcpy](../../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)

- [memset](../../c-runtime-library/reference/memset-wmemset.md)

- [memcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)， [wmemcpy](../../c-runtime-library/reference/memcpy-wmemcpy.md)

当参数转换为更大的数据类型，并请从左值引用进行复制赋值，也会出现警告。

VisualC++可能会生成此警告永远不会执行的代码路径。 可以使用 `#pragma` 临时禁用该警告，如此示例中所示：

```cpp
#pragma warning( push )
#pragma warning( disable : 4789 )
// unused code that generates compiler warning C4789`
#pragma warning( pop )
```

此习惯用法保留 VisualC++生成的警告的该特定代码块。 `#pragma warning(push)` 会在 `#pragma warning(disable: 4789)` 更改现有状态之前保留该状态。 `#pragma warning(pop)` 会还原压入的状态，并移除 `#pragma warning(disable:4789)` 的效果。 有关详细信息C++预处理器指令`#pragma`，请参阅[警告](../../preprocessor/warning.md)并[杂注指令和 __Pragma 关键字](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)。

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

void main()
{
   int * p = (int *)&G;
   *p = 3;   // C4789 - writes an int through a pointer to short
}
```