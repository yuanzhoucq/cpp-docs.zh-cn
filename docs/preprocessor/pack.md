---
title: pack 杂注
ms.date: 07/22/2020
f1_keywords:
- pack_CPP
- vc-pragma.pack
helpviewer_keywords:
- pragmas, pack
- pack pragma
ms.assetid: e4209cbb-5437-4b53-b3fe-ac264501d404
ms.openlocfilehash: 72f94520516cce2ae36b70795fb29e3d4d8068df
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219386"
---
# <a name="pack-pragma"></a>pack 杂注

指定结构、联合和类成员的封装对齐方式。

## <a name="syntax"></a>语法

> **`#pragma pack( show )`**\
> **`#pragma pack( push`** [ **`,`** *`identifier`* ] [ **`,`** *`n`* ] **`)`**\
> **`#pragma pack( pop`** [ **`,`** { *`identifier`* | *`n`* } ] **`)`**\
> **`#pragma pack(`** [ *`n`* ] **`)`**

### <a name="parameters"></a>参数

**`show`**\
可有可无显示打包对齐的当前字节值。 该值由警告消息显示。

**`push`**\
可有可无将当前封装对齐值推送到内部编译器堆栈上，并将当前封装对齐值设置为*n*。 如果未指定*n* ，则推送当前封装对齐值。

**`pop`**\
可有可无从内部编译器堆栈的顶部移除记录。 如果未指定*n* **`pop`** ，则与堆栈顶部的结果记录关联的封装值是新的封装对齐值。 例如，如果指定了*n* ，则 `#pragma pack(pop, 16)` *n*会成为新的封装对齐值。 例如，如果您使用的是，例如，则 *`identifier`* `#pragma pack(pop, r1)` 会弹出堆栈上的所有记录，直到找到具有的记录 *`identifier`* 。 该记录会弹出，与堆栈顶部找到的记录关联的封装值将成为新的封装对齐值。 如果你使用在 *`identifier`* 堆栈上的任何记录中都找不到的，则 **`pop`** 将忽略。

语句 `#pragma pack (pop, r1, 2)` 等效于 `#pragma pack (pop, r1)` 后跟 `#pragma pack(2)` 。

*`identifier`*\
可有可无当与一起使用时，将为 **`push`** 内部编译器堆栈上的记录指定一个名称。 当与一起使用时 **`pop`** ，将在删除之前从内部堆栈中弹出记录 *`identifier`* 。 如果 *`identifier`* 在内部堆栈上找不到，则不会弹出任何内容。

*`n`*\
可有可无指定要用于打包的值（以字节为单位）。 如果 [`/Zp`](../build/reference/zp-struct-member-alignment.md) 没有为模块设置编译器选项，则的默认值 *`n`* 为8。 有效值为 1、2、4、8 和 16。 成员的对齐方式在一个边界上，该边界是的倍数 *`n`* 或成员大小的倍数，以较小者为准。

## <a name="remarks"></a>备注

*打包*类是将其成员彼此直接放置在内存中。 这可能意味着，某些或全部成员可以在小于目标体系结构的默认对齐方式的边界上对齐。 **`pack`** 在数据声明级别提供控件。 它不同于编译器选项 [`/Zp`](../build/reference/zp-struct-member-alignment.md) ，后者仅提供模块级控件。 **pack**在 **`struct`** 检测到 **`union`** 杂注后，pack 会在第一个、或声明处生效 **`class`** 。 **`pack`** 对定义不起作用。 **`pack`** 不带任何参数的调用会将设置 *`n`* 为编译器选项中设置的值 **`/Zp`** 。 如果未设置编译器选项，则 x86、ARM 和 ARM64 的默认值为8。 对于 x64 本机，默认值为16。

如果更改结构的对齐方式，则它可能不会在内存中占用大量空间。 但是，你可能会发现性能损失，甚至会获得硬件生成的异常来实现未对齐的访问。 您可以使用修改此异常行为 [`SetErrorMode`](/windows/win32/api/errhandlingapi/nf-errhandlingapi-seterrormode) 。

有关如何修改对齐方式的详细信息，请参阅以下文章：

- [`alignof`](../cpp/alignof-operator.md)

- [`align`](../cpp/align-cpp.md)

- [`__unaligned`](../cpp/unaligned.md)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)（特定于 x64）

   > [!WARNING]
   > 在 Visual Studio 2015 和更高版本中，你可以使用标准 **`alignas`** 和 **`alignof`** 运算符，这一点与 **`__alignof`** **`__declspec( align )`** 在编译器间可移植性不同。 C + + 标准不寻址打包，因此您仍必须使用 **`pack`** （或其他编译器上相应的扩展）来指定小于目标体系结构的单词大小的对齐方式。

## <a name="examples"></a>示例

下面的示例演示如何使用 **`pack`** 杂注更改结构的对齐方式。

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

## <a name="see-also"></a>另请参阅

[Pragma 指令和 `__pragma` 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
