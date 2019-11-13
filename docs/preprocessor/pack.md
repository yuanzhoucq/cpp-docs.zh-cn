---
title: 包装杂注
ms.date: 11/11/2019
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 3572bd0d0b0e8149f527c1c43eca5870783b13a8
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965248"
---
# <a name="pack-pragma"></a>包装杂注

指定结构、联合和类成员的封装对齐方式。

## <a name="syntax"></a>语法

> **#pragma pack （show）** \
> **#pragma pack （push** [ **，** *identifier* ] [ **，** *n* ] **）** \
> **#pragma pack （pop** [ **，** {*标识符* | *n* }] **）** \
> **#pragma pack （** [ *n* ] **）**

### <a name="parameters"></a>参数

**显示**\
可有可无显示打包对齐的当前字节值。 该值由警告消息显示。

**推送**\
可有可无将当前封装对齐值推送到内部编译器堆栈上，并将当前封装对齐值设置为*n*。 如果未指定*n* ，则推送当前封装对齐值。

**pop**\
可有可无从内部编译器堆栈的顶部移除记录。 如果未用**pop**指定*n* ，则与堆栈顶部的结果记录关联的封装值是新的封装对齐值。 如果指定了*n* ，如 `#pragma pack(pop, 16)`，则*n*将成为新的封装对齐值。 如果使用*标识符*（例如 `#pragma pack(pop, r1)`）进行弹出，则会弹出堆栈上的所有记录，直到找到具有*标识符*的记录。 将弹出该记录，并且与堆栈顶部的结果记录关联的封装值是新的封装对齐值。 如果你使用在堆栈上的任何记录中都找不到的*标识符*来进行弹出，则会忽略**pop** 。 

语句 `#pragma pack (pop, r1, 2)` 等效于 `#pragma pack (pop, r1)` 后跟 `#pragma pack(2)`。

*标识符*\
可有可无与**push**一起使用时，将为内部编译器堆栈上的记录指定一个名称。 当与**pop**一起使用时，将在内部堆栈中弹出记录，直到删除*标识符*。 如果在内部堆栈上找不到*标识符*，则不会弹出任何内容。

*n*\
可有可无指定要用于打包的值（以字节为单位）。 如果没有为模块设置编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md) ，则*n*的默认值为8。 有效值为 1、2、4、8 和 16。 成员的对齐方式在一个边界上，该边界是*n*的倍数或该成员大小的倍数，以较小者为准。

## <a name="remarks"></a>备注

*打包*类是将其成员彼此直接放置在内存中。 这可能意味着，某些或全部成员可以在小于目标体系结构的默认对齐方式的边界上对齐。 **pack**为数据声明级别提供控制。 它不同于编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md)，后者仅提供模块级控件。 在检测到杂注后， **pack**会在第一个**结构**、**联合**或**类**声明上生效。 **pack**对定义没有任何影响。 调用不带参数的**pack**会将*n*设置为编译器选项 `/Zp`中设置的值。 如果未设置编译器选项，则默认值为8。

如果更改某个结构的对齐方式，它可能不会使用像内存中一样多的空间，但您可能会发现性能降低或者甚至是因未对齐访问而遇到硬件产生的异常。  可以使用[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)修改此异常行为。

有关如何修改对齐方式的详细信息，请参阅以下文章：

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)（特定于 x64）

   > [!WARNING]
   > 在 Visual Studio 2015 和更高版本中，你可以使用标准的**alignas**和**alignof**运算符，这与 `__alignof` 和 `declspec( align )` 可在编译器之间移植。 C++标准并不寻址打包，因此您仍然必须使用**pack** （或其他编译器上相应的扩展）来指定小于目标体系结构的单词大小的对齐方式。

## <a name="examples"></a>示例

下面的示例演示如何使用**pack**杂注更改结构的对齐方式。

```cpp
// pragma_directives_pack.cpp
#include <stddef.h>
#include <stdio.h>

struct S {
   int i;   // size 4
   short j;   // size 2
   double k;   // size 8
};

#pragma pack(2)
struct T {
   int i;
   short j;
   double k;
};

int main() {
   printf("%zu ", offsetof(S, i));
   printf("%zu ", offsetof(S, j));
   printf("%zu\n", offsetof(S, k));

   printf("%zu ", offsetof(T, i));
   printf("%zu ", offsetof(T, j));
   printf("%zu\n", offsetof(T, k));
}
```

```Output
0 4 8
0 4 6
```

下面的示例演示如何使用*push*、 *pop*和*show*语法。

```cpp
// pragma_directives_pack_2.cpp
// compile with: /W1 /c
#pragma pack()   // n defaults to 8; equivalent to /Zp8
#pragma pack(show)   // C4810
#pragma pack(4)   // n = 4
#pragma pack(show)   // C4810
#pragma pack(push, r1, 16)   // n = 16, pushed to stack
#pragma pack(show)   // C4810

// pop to the identifier and then set
// the value of the current packing alignment:
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)