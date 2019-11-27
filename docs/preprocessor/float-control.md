---
title: float_control 杂注
description: 描述 float_control 杂注指令的用法和效果。 Float_control 指令在运行时控制浮点精确语义和异常语义的状态。
ms.date: 11/18/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 0c9caea5ba35a55a53f7b9340cf9bfd2cce80561
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305504"
---
# <a name="float_control-pragma"></a>float_control 杂注

指定函数的浮点行为。

## <a name="syntax"></a>语法

> **#pragma float_control**\
> **#pragma float_control （精确、** { **on** | **off** } [ **，push** ] **）** \
> **#pragma float_control （除** ** | ** **off** } [ **，push** ] **）** \
> **#pragma float_control （** { **push** | **pop** } **）**

## <a name="options"></a>Options

**精确** |  **关闭**，**推送**\
指定是启用（**on**）还是禁用（**关闭**）精确浮点语义。 有关此选项与类似的 " **/fp：精确**编译器" 选项的区别的信息，请参阅 "备注" 部分。 可选的**推送**标记告知编译器在内部编译器堆栈上推送**float_control**的当前设置。

**除** | **off** **时**，**推送**\
指定启用（**on**）还是禁用（**关闭**）浮点异常语义。 有关此选项与类似的 " **/fp： except** " 选项的区别的信息，请参阅 "备注" 部分。 可选的**推送**标记告知编译器在内部编译器堆栈上推送**float_control**的当前设置。

当 "**精确**" 也设置为 **"开**" 时，**仅可将**设置为 **"开"** 。

**推送**\
将当前**float_control**设置推送到内部编译器堆栈上。

**pop**\
从内部编译器堆栈的顶部移除**float_control**设置，并使其成为新的**float_control**设置。

## <a name="remarks"></a>备注

"**精确**" 和 "**除外**" 选项没有与相同名称的[/fp](../build/reference/fp-specify-floating-point-behavior.md)编译器选项完全相同的行为。 **Float_control**杂注仅管辖部分浮点行为。 它必须与[fp_contract](../preprocessor/fp-contract.md)和[fenv_access](../preprocessor/fenv-access.md)杂注结合，才能重新创建 **/fp**编译器选项。 下表显示了每个编译器选项的等效杂注设置：

| | float_control （精确、\*） | float_control （\*除外） | fp_contract （\*） | fenv_access （\*） |
|-|-|-|-|-|
| /fp:strict             | 启用  | 启用  | 非 | 启用  |
| /fp:strict /fp:except- | 启用  | 非 | 非 | 启用  |
| /fp:precise            | 启用  | 非 | 启用  | 非 |
| /fp：精确/fp： except | 启用  | 启用  | 启用  | 非 |
| /fp:fast               | 非 | 非 | 启用  | 非 |

换句话说，您必须结合使用多个杂注来模拟 **/fp： fast**、 **/fp：精确**、 **/fp： strict**和 **/fp：** 命令行选项除外。

结合使用**float_control**和**fenv_access**浮点杂注的方式有一些限制：

- 仅当启用了精确**语义时，** 才能使用**float_control**来设置**除外**。 可以通过**float_control**杂注或使用 **/fp：精确**或 **/fp： strict**编译器选项来启用精确语义。

- 如果启用了异常语义，则不能使用**float_control**关闭**精确**的功能，无论是通过**float_control** pragma 还是 **/fp： except**编译器选项。

- 除非启用了精确语义，否则不能启用**fenv_access** ，无论是通过**float_control**杂注还是编译器选项启用。

- 启用**fenv_access**时，不能使用**float_control**来**精确**关闭。

这些限制意味着某些浮点杂注的顺序非常重要。 若要使用**float_control**和相关杂注从快速模型转为严格模型，请使用以下代码：

```cpp
#pragma float_control(precise, on)  // enable precise semantics
#pragma fenv_access(on)             // enable environment sensitivity
#pragma float_control(except, on)   // enable exception semantics
#pragma fp_contract(off)            // disable contractions
```

若要使用**float_control**杂注从严格模型转为快速模型，请使用以下代码：

```cpp
#pragma float_control(except, off)  // disable exception semantics
#pragma fenv_access(off)            // disable environment sensitivity
#pragma float_control(precise, off) // disable precise semantics
#pragma fp_contract(on)             // ensable contractions
```

如果未指定任何选项， **float_control**将不起作用。

## <a name="example"></a>示例

下面的示例演示如何使用杂注**float_control**捕获溢出浮点异常。

```cpp
// pragma_directive_float_control.cpp
// compile with: /EHa
#include <stdio.h>
#include <float.h>

double func( ) {
   return 1.1e75;
}

#pragma float_control (except, on)

int main( ) {
   float u[1];
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, ~_EM_OVERFLOW, _MCW_EM);
   if (err != 0)
      printf_s("_controlfp_s failed!\n");

   try  {
      u[0] = func();
      printf_s ("Fail");
      return(1);
   }

   catch (...)  {
      printf_s ("Pass");
      return(0);
   }
}
```

```Output
Pass
```

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[fenv_access](../preprocessor/fenv-access.md)\
[fp_contract](../preprocessor/fp-contract.md)
