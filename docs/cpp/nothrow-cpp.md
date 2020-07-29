---
title: nothrow (C++)
ms.date: 01/03/2018
f1_keywords:
- nothrow_cpp
helpviewer_keywords:
- __declspec keyword [C++], nothrow
- nothrow __declspec keyword
ms.assetid: 0a475139-459c-4ec6-99e8-7ecd0d7f44a3
ms.openlocfilehash: 8ce0e9ea6a39ef7760c7a6d0802913326433cf68
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87227265"
---
# <a name="nothrow-c"></a>nothrow (C++)

**Microsoft 专用**

**`__declspec`** 可在函数声明中使用的扩展属性。

## <a name="syntax"></a>语法

> *返回类型*__declspec （nothrow） [*调用约定*]*函数名称*（[*参数列表*]）

## <a name="remarks"></a>备注

建议所有新代码使用[noexcept](noexcept-cpp.md)运算符而不是 `__declspec(nothrow)` 。

此特性告知编译器，声明的函数及其调用的函数从不引发异常。 但是，它不强制执行指令。 换句话说，它永远不会导致调用[std：： terminate](../standard-library/exception-functions.md#terminate) ，这与 **`noexcept`** 或在**std： c + + 17**模式（Visual Studio 2017 版本15.5 及更高版本）中 `throw()` 。

利用当前默认的同步异常处理模式，编译器可以消除跟踪此类函数中的某些不可展开的对象的生命周期的机制，从而显著减小代码大小。 给定以下预处理器指令，下面的三个函数声明在 **/std： c + + 14**模式下等效：

```cpp
#define WINAPI __declspec(nothrow) __stdcall

void WINAPI f1();
void __declspec(nothrow) __stdcall f2();
void __stdcall f3() throw();
```

在 **/std 中： c + + 17**模式下， `throw()` 与使用的其他模式不等效， `__declspec(nothrow)` 因为 `std::terminate` 如果函数引发异常，则会调用它。

`void __stdcall f3() throw();`声明使用 c + + 标准定义的语法。 在 c + + 17 中， `throw()` 关键字已弃用。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[__declspec](../cpp/declspec.md)<br/>
[noexcept](noexcept-cpp.md)<br/>
[关键字](../cpp/keywords-cpp.md)
