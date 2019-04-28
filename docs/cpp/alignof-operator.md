---
title: __alignof 运算符
ms.date: 12/17/2018
f1_keywords:
- alignas_cpp
- __alignof_cpp
- alignof_cpp
- __alignof
- _alignof
helpviewer_keywords:
- alignas [C++]
- alignment of structures
- __alignof keyword [C++]
- alignof [C++]
- types [C++], alignment requirements
ms.assetid: acb1eed7-6398-40bd-b0c5-684ceb64afbc
ms.openlocfilehash: 96c85db83c133af6f1712baa8597ed3360277854
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62258247"
---
# <a name="alignof-operator"></a>__alignof 运算符

C + + 11 引入了**alignof**返回的对齐方式，以字节为单位指定类型的运算符。 为实现最大的可移植性，应使用 alignof 运算符，而不是特定于 Microsoft 的 __alignof 运算符。

**Microsoft 专用**

返回类型的值`size_t`类型的对齐要求。

## <a name="syntax"></a>语法

```cpp
  __alignof( type )
```

## <a name="remarks"></a>备注

例如：

|表达式|“值”|
|----------------|-----------|
|**__alignof( char )**|1|
|**__alignof( short )**|2|
|**__alignof( int )**|4|
|**__alignof( \__int64 )**|8|
|**__alignof( float )**|4|
|**__alignof( double )**|8|
|**__alignof( char\* )**|4|

**__Alignof**值是相同的值为`sizeof`针对基本类型。 但是，请考虑该示例：

```cpp
typedef struct { int a; double b; } S;
// __alignof(S) == 8
```

在这种情况下， **__alignof**值是结构中的最大元素的对齐需求。

同样，

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`__alignof(S)` 等于 `32`。

一个用于 **__alignof**会作为一个自己的内存分配例程的参数。 例如，假定下面定义的结构 `S`，您可以调用名为 `aligned_malloc` 的内存分配例程以在特定对齐边界上分配内存。

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), __alignof(S));
```

与以前版本的兼容性 **_alignof**是的同义词 **__alignof**除非编译器选项[/Za\(禁用语言扩展)](../build/reference/za-ze-disable-language-extensions.md)是指定。

有关修改对齐方式的详细信息，请参阅：

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp（结构成员对齐）](../build/reference/zp-struct-member-alignment.md)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)(特定于 x64)

有关 x86 和 x64 代码中的对齐方式的差异的详细信息，请参阅：

- [与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)