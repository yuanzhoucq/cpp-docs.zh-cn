---
title: naked (C++)
ms.date: 11/04/2016
f1_keywords:
- naked_cpp
helpviewer_keywords:
- __declspec keyword [C++], naked
- naked __declspec keyword
ms.assetid: 69723241-05e1-439b-868e-20a83a16ab6d
ms.openlocfilehash: cff2455608966886e9c5b07039dff439538caefe
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227330"
---
# <a name="naked-c"></a>naked (C++)

**Microsoft 专用**

对于用特性声明的函数 **`naked`** ，编译器生成不带 prolog 和 epilog 代码的代码。 利用此功能，可以使用内联汇编程序代码编写您自己的 prolog/epilog 代码序列。 裸函数对于编写虚拟设备驱动程序特别有用。  请注意，该 **`naked`** 属性仅在 x86 和 ARM 上有效，在 x64 上不可用。

## <a name="syntax"></a>语法

```
__declspec(naked) declarator
```

## <a name="remarks"></a>备注

由于 **`naked`** 特性仅与函数的定义相关且不是类型修饰符，因此，裸函数必须使用扩展的特性语法和[__declspec](../cpp/declspec.md)关键字。

编译器无法为使用裸特性标记的函数生成内联函数，即使该函数也标记有[__forceinline](inline-functions-cpp.md)关键字。

如果将 **`naked`** 特性应用于非成员方法的定义之外的任何内容，则编译器会发出错误。

## <a name="examples"></a>示例

此代码使用特性定义函数 **`naked`** ：

```
__declspec( naked ) int func( formal_parameters ) {}
```

或：

```
#define Naked __declspec( naked )
Naked int func( formal_parameters ) {}
```

**`naked`** 特性仅影响函数的 prolog 和 epilog 序列的编译器代码生成的性质。 它不影响为调用这些函数而生成的代码。 因此， **`naked`** 特性不被视为函数类型的一部分，并且函数指针不能具有 **`naked`** 特性。 此外， **`naked`** 特性不能应用于数据定义。 例如，下面的代码示例生成一个错误：

```
__declspec( naked ) int i;
// Error--naked attribute not permitted on data declarations.
```

**`naked`** 特性仅与函数的定义相关，不能在函数的原型中指定。 例如，下面的声明生成编译器错误：

```
__declspec( naked ) int func();  // Error--naked attribute not permitted on function declarations
```

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[关键字](../cpp/keywords-cpp.md)<br/>
[Naked 函数调用](../cpp/naked-function-calls.md)
