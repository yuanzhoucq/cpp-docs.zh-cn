---
title: managed、unmanaged 杂注
ms.date: 08/29/2019
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
ms.openlocfilehash: 4c13155d1c84966a593df11baf525a0c3539f02c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218810"
---
# <a name="managed-unmanaged-pragmas"></a>managed、unmanaged 杂注

启用函数级控件以将函数编译为托管或非托管。

## <a name="syntax"></a>语法

> **#pragma 托管**\
> **#pragma 非托管**\
> **#pragma 托管 (** [**推送,** ] { **on** | **off** } **)** \
> **#pragma 托管 (pop)**

## <a name="remarks"></a>备注

[/Clr](../build/reference/clr-common-language-runtime-compilation.md)编译器选项提供用于将函数编译为托管或非托管的模块级控件。

将为本机平台编译非托管函数。 此部分程序的执行将由公共语言运行时传递给本机平台。

当使用了 `/clr` 时，默认情况下将函数编译为托管函数。

在将应用这些杂注时：

- 将杂注添加到函数之前, 而不是在函数体中。

- 在 `#include`语句后添加杂注。 请不要在语句前`#include`使用这些杂注。

如果`/clr`编译中未使用**托管**和**非托管**杂注, 编译器将忽略它们。

当对模板函数进行实例化时, 在定义模板时, 杂注状态将确定其是否为托管或非托管。

有关详细信息, 请参阅[混合程序集的初始化](../dotnet/initialization-of-mixed-assemblies.md)。

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

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
