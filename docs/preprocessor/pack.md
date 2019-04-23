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
ms.openlocfilehash: bf1ae81184d53dd271f63c26e8f9a52a6410b232
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/18/2019
ms.locfileid: "59038442"
---
# <a name="pack"></a>pack
指定结构、联合和类成员的封装对齐。

## <a name="syntax"></a>语法

```
#pragma pack( [ show ] | [ push | pop ] [, identifier ] , n  )
```

### <a name="parameters"></a>参数

**show**<br/>
（可选）显示封装对齐的当前字节值。 该值由警告消息显示。

**push**<br/>
（可选）推送当前封装对齐值上的内部编译器堆栈和当前封装对齐值的设置为*n*。 如果*n*未指定，则当前封装对齐值推送。

**pop**<br/>
（可选）从内部编译器堆栈的顶部移除记录。 如果*n*未与指定**pop**，则与堆栈顶部的生成的记录关联的封装值是新封装对齐值。 如果*n*指定，例如， `#pragma pack(pop, 16)`， *n*将成为新封装对齐值。 如果你使用弹出*标识符*，例如`#pragma pack(pop, r1)`，然后在堆栈上的所有记录将都弹出，直到已记录*标识符*找到。 该记录将会弹出，与堆栈顶部的生成的记录关联的封装值是新的封装对齐值。 如果你使用弹出*标识符*在堆栈上的任何记录中未找到，则**pop**将被忽略。

*identifier*<br/>
（可选）与一起使用时*推送*，将名称分配给内部编译器堆栈上的记录。 与一起使用时**pop**，弹出之前内部堆栈中弹出记录*标识符*被删除; 如果*标识符*中找不到内部堆栈中，会弹出任何内容。

*n*<br/>
（可选）指定值，以字节为单位，用于封装。 如果编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md)模块的默认值为未设置*n*为 8。 有效值为 1、2、4、8 和 16。 成员的对齐方式的倍数的边界，则为*n*或成员的大小的倍数小者为准。

`#pragma pack(pop, identifier, n)` 未定义。

## <a name="remarks"></a>备注

封装类是在内存中将其一个成员直接放在另一个后面，这可能表示对齐部分或全部成员的边界可以小于默认对齐目标体系结构。 **包**提供了数据声明级别的控制。 这不同于编译器选项[/Zp](../build/reference/zp-struct-member-alignment.md)，只提供模块级别控制。 **包**第一处生效**struct**，**联合**，或**类**声明后杂注。 **包**对定义没有影响。 调用**pack**使用任何参数集*n*编译器选项中设置的值为`/Zp`。 如果未设置编译器选项，则默认值为 8。

如果更改某个结构的对齐方式，它可能不会使用像内存中一样多的空间，但您可能会发现性能降低或者甚至是因未对齐访问而遇到硬件产生的异常。  您可以通过修改此异常行为[SetErrorMode](https://msdn.microsoft.com/library/windows/desktop/ms680621)。

有关如何修改对齐方式的详细信息，请参阅以下主题：

- [__alignof](../cpp/alignof-operator.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)(特定于 x64)

   > [!WARNING]
   > 请注意，在 Visual Studio 2015 和更高版本可使用标准的 alignas 和 alignof 运算符，这 不同于 `__alignof` 和 `declspec( align )`，它们是跨编译器可移植的。 C++标准不能解决封装，因此仍必须使用**pack** （或其他编译器上相应的扩展） 来指定小于目标体系结构的字大小的对齐方式。

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

下面的示例演示如何使用*推送*， *pop*，并*显示*语法。

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