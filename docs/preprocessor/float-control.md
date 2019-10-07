---
title: float_control 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: aa8cdc07953405175c1753791ab53214d73ba516
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218578"
---
# <a name="float_control-pragma"></a>float_control 杂注

指定函数的浮点行为。

## <a name="syntax"></a>语法

> **#pragma float_control**\
> **#pragma float_control (** {**除} 之外** **的** |  | 精确 strict 除外} [, push]) | \
> **#pragma float_control (** { **push** | **pop** } **)**

## <a name="options"></a>选项

**精确** **严格限制** **, 在**off 时,推送 |  |  | \
指定浮点行为, 该行为可以是**精确**、**严格**或**除外**。 有关详细信息，请参阅 [/fp（指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。 设置可以为 **"打开"** 或 "**关闭**"。

**严格**的情况下, "**打开**" 或 "**关闭**" 设置指定了**strict**和**except**的设置。 当 "**精确**" 或 " **strict** " 也设置为 **"开**" 时, 只能将设置为**on** 。

如果添加了可选的**推送**令牌, 则**float_control**的当前设置将推送到内部编译器堆栈上。

**请求**\
将当前**float_control**设置推送到内部编译器堆栈

**弹出**\
从内部编译器堆栈的顶部移除**float_control**设置, 并使其成为新的**float_control**设置。

## <a name="remarks"></a>备注

当 on**除外**时, 不能使用**float_control**将其关闭。 同样, 如果[fenv_access](../preprocessor/fenv-access.md)为 on, 则无法关闭**精确**的。 若要使用**float_control**杂注从严格模型转为快速模型, 请使用以下代码:

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

若要使用**float_control**杂注从 fast 模型转为严格模型, 请使用以下代码:

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

如果未指定任何选项, 则**float_control**不起作用。

其他浮点杂注包括：

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

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

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
