---
title: alignof 运算符
ms.date: 12/17/2018
f1_keywords:
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
ms.openlocfilehash: 6a2046774674858211ae89abb9b4cfc7b09c0a6d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227629"
---
# <a name="alignof-operator"></a>alignof 运算符

**`alignof`** 运算符将指定类型的对齐方式返回为类型的值 **`size_t`** 。

## <a name="syntax"></a>语法

```cpp
alignof( type )
```

## <a name="remarks"></a>备注

例如：

| 表达式 | 值 |
|--|--|
| **`alignof( char )`** | 1 |
| **`alignof( short )`** | 2 |
| **`alignof( int )`** | 4 |
| **`alignof( long long )`** | 8 |
| **`alignof( float )`** | 4 |
| **`alignof( double )`** | 8 |

**`alignof`** 值与 **`sizeof`** 用于基本类型的值相同。 但是，请考虑该示例：

```cpp
typedef struct { int a; double b; } S;
// alignof(S) == 8
```

在这种情况下， **`alignof`** 值是结构中的最大元素的对齐要求。

同样，

```cpp
typedef __declspec(align(32)) struct { int a; } S;
```

`alignof(S)` 等于 `32`。

一种用途 **`alignof`** 是作为自己的内存分配例程之一的参数。 例如，假定下面定义的结构 `S`，您可以调用名为 `aligned_malloc` 的内存分配例程以在特定对齐边界上分配内存。

```cpp
typedef __declspec(align(32)) struct { int a; double b; } S;
int n = 50; // array size
S* p = (S*)aligned_malloc(n * sizeof(S), alignof(S));
```

有关修改对齐方式的详细信息，请参阅：

- [pack](../preprocessor/pack.md)

- [align](../cpp/align-cpp.md)

- [__unaligned](../cpp/unaligned.md)

- [/Zp （结构成员对齐）](../build/reference/zp-struct-member-alignment.md)

- [结构对齐示例](../build/x64-software-conventions.md#examples-of-structure-alignment)（特定于 x64）

有关 x86 和 x64 代码中的对齐方式的差异的详细信息，请参阅：

- [与 x86 编译器冲突](../build/x64-software-conventions.md#conflicts-with-the-x86-compiler)

### <a name="microsoft-specific"></a>Microsoft 专用

**`alignof`** 和 **`__alignof`** 是 Microsoft 编译器中的同义词。 在 c + + 11 中成为标准的一部分之前，特定于 Microsoft 的 **`__alignof`** 操作员提供此功能。 为了获得最大的可移植性，应使用 **`alignof`** 运算符而不是特定于 Microsoft 的 **`__alignof`** 运算符。

对于与以前版本的兼容性，为， **`_alignof`** **`__alignof`** 除非指定编译器选项 " [ `/Za` \( 禁用语言扩展](../build/reference/za-ze-disable-language-extensions.md)"，否则将是同义词。

## <a name="see-also"></a>请参阅

[使用一元运算符的表达式](../cpp/expressions-with-unary-operators.md)<br/>
[关键字](../cpp/keywords-cpp.md)
