---
title: managed、unmanaged
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 7fa1e3274b85faa9f3f72f4db5bf586ee5d8e274
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022341"
---
# <a name="managed-unmanaged"></a>managed、unmanaged
启用函数级控制以将函数编译为托管或未托管函数。

## <a name="syntax"></a>语法

```
#pragma managed
#pragma unmanaged
#pragma managed([push,] on | off)
#pragma managed(pop)
```

## <a name="remarks"></a>备注

[/Clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项提供用于编译为托管或非托管函数的模块级控制。

未托管函数将为本机平台编译，因此，这一部分的程序的执行将由公共语言运行时传递给本机平台。

当使用了 `/clr` 时，默认情况下将函数编译为托管函数。

在将应用这些杂注时：

- 在函数前添加杂注，而不是在函数体内添加。

- 在 `#include`语句后添加杂注。 在 `#include` 语句之前不使用这些杂注。

编译器将忽略**托管**并**非托管**杂注如果`/clr`不编译中使用。

当实例化模板函数后，定义时的模板的杂注状态可确定该函数是托管或未托管的。

有关详细信息，请参阅[混合程序集初始化](../dotnet/initialization-of-mixed-assemblies.md)。

## <a name="example"></a>示例

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>请参阅

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)