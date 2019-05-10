---
title: float_control
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.float_control
- float_control_CPP
helpviewer_keywords:
- float_control pragma
- pragmas, float_control
ms.assetid: 4f4ba5cf-3707-413e-927d-5ecdbc0a9a43
ms.openlocfilehash: 8a7829252cebb726363c67c990a94d08b0d6467a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389211"
---
# <a name="floatcontrol"></a>float_control

指定函数的浮点行为。

## <a name="syntax"></a>语法

> **#pragma float_control** [ **(** [ *value* **,** *setting* [ **, push** ] ] | [ **push** | **pop** ] **)** ]

## <a name="options"></a>选项

*value*, *setting* [, **push**]<br/>
指定浮点行为。 *值*可以是**精确**，**严格**，或**除**。 有关详细信息，请参阅 [/fp（指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。 *设置*可以处于**上**或**关闭**。

如果*值*是**严格**，同时设置**严格**并**除**由指定*设置*. **除**只能设置为**上**时**精确**或**严格**也设置为**上**。

如果可选**推送**令牌添加，当前设置为*值*推送到内部编译器堆栈。

**push**<br/>
推送当前**float_control**设置到内部编译器堆栈

**pop**<br/>
移除**float_control**从内部编译器堆栈的顶部设置，并成为新**float_control**设置。

## <a name="remarks"></a>备注

不能使用**float_control**以打开**精确**关闭时**除**上。 同样，**精确**无法关闭时[fenv_access](../preprocessor/fenv-access.md)上。 若要从严格模式转到快速模式通过使用**float_control**杂注，使用以下代码：

```cpp
#pragma float_control(except, off)
#pragma fenv_access(off)
#pragma float_control(precise, off)
```

若要从快速模式转到严格模式，与**float_control**杂注，使用以下代码：

```cpp
#pragma float_control(precise, on)
#pragma fenv_access(on)
#pragma float_control(except, on)
```

如果未不指定任何选项， **float_control**不起作用。

其他浮点杂注包括：

- [fenv_access](../preprocessor/fenv-access.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="example"></a>示例

下面的示例演示如何通过使用杂注捕获溢出浮点异常**float_control**。

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

[Pragma 指令和 __Pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
