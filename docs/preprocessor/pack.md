---
title: pack
ms.date: 12/17/2018
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: da4484ec86d39c8fa55a741eadd53a1d614b20dc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510174"
---
# <a name="pack"></a>pack
指定结构、联合和类成员的封装对齐。

## <a name="syntax"></a>语法

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>参数

**show**<br/>
可有可无显示打包对齐的当前字节值。 该值由警告消息显示。

**push**<br/>
可有可无将当前封装对齐值推送到内部编译器堆栈上, 并将当前封装对齐值设置为*n*。 如果未指定*n* , 则推送当前封装对齐值。

**pop**<br/>
可有可无从内部编译器堆栈的顶部移除记录。 如果未用**pop**指定*n* , 则与堆栈顶部的结果记录关联的封装值是新的封装对齐值。 例如 `#pragma pack(pop, 16)`, 如果指定了 n, 则*n*会成为新的封装对齐值。 如果您用*标识符*(例如`#pragma pack(pop, r1)`,) 弹出, 则会弹出堆栈上的所有记录, 直到找到具有*标识符*的记录。 该记录将会弹出，与堆栈顶部的生成的记录关联的封装值是新的封装对齐值。 如果你使用在堆栈上的任何记录中都找不到的*标识符*弹出消息, 则将忽略**pop** 。

*identifier*<br/>
可有可无与*push*一起使用时, 将为内部编译器堆栈上的记录指定一个名称。 当与**pop**一起使用时, 将在内部堆栈中弹出记录, 直到删除*标识符*;如果在内部堆栈上找不到*标识符*, 则不会弹出任何内容。

*n*<br/>
可有可无指定要用于打包的值 (以字节为单位)。 如果没有为模块设置编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md) , 则*n*的默认值为8。 有效值为 1、2、4、8 和 16。 成员的对齐方式将位于边界, 该边界是*n*的倍数或该成员大小的倍数, 以较小者为准。

`#pragma pack(pop, identifier, n)`未定义。

## <a name="remarks"></a>备注

封装类是在内存中将其一个成员直接放在另一个后面，这可能表示对齐部分或全部成员的边界可以小于默认对齐目标体系结构。 **pack**为数据声明级别提供控制。 这不同于编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md), 后者仅提供模块级控件。 在检测到杂注后, **pack**会在第一个**结构**、**联合**或**类**声明上生效。 **pack**对定义没有任何影响。 调用不带参数的**pack**会将*n*设置为编译器选项`/Zp`中设置的值。 如果未设置编译器选项，则默认值为 8。

如果更改某个结构的对齐方式，它可能不会使用像内存中一样多的空间，但您可能会发现性能降低或者甚至是因未对齐访问而遇到硬件产生的异常。  可以使用[SetErrorMode](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode)修改此异常行为。

有关如何修改对齐方式的详细信息，请参阅以下主题：

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)(x64 特定)

   > [!WARNING]
   > 请注意，在 Visual Studio 2015 和更高版本可使用标准的 alignas 和 alignof 运算符，这 不同于 `__alignof` 和 `declspec( align )`，它们是跨编译器可移植的。 C++标准版不会寻址打包, 因此您仍然必须使用**pack** (或其他编译器上的相应扩展名) 来指定小于目标体系结构的单词大小的对齐方式。

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
#pragma pack(pop, r1, 2)   // n = 2 , stack popped
#pragma pack(show)   // C4810
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)