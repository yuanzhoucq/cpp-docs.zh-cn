---
title: fenv_access 杂注
description: 描述 fenv_access 杂注指令的用法和效果。 Fenv_access 指令控制在运行时对浮点环境的访问。
ms.date: 11/19/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: e03eb404f2805a4f7c96509600c063c1b1acf629
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305856"
---
# <a name="fenv_access-pragma"></a>fenv_access 杂注

禁用（**启用**）或启用（**关闭**）可更改浮点环境标志测试和模式更改的优化。

## <a name="syntax"></a>语法

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>备注

默认情况下， **fenv_access**处于**关闭状态**。 编译器假设您的代码不访问或操作浮点环境。 如果不需要环境访问，编译器可以执行更多操作来优化你的浮点代码。

如果你的代码测试浮点状态标志、异常或设置控件模式标志，则启用**fenv_access** 。 编译器禁用浮点优化，因此您的代码可以一致地访问浮点环境。

[/Fp： strict] 命令行选项可自动启用**fenv_access**。 有关此和其他浮点行为的详细信息，请参阅[/fp （指定浮点行为）](../build/reference/fp-specify-floating-point-behavior.md)。

将**fenv_access**杂注与其他浮点设置结合使用的方式有一些限制：

- 除非启用了精确语义，否则不能启用**fenv_access** 。 可以通过[float_control](float-control.md)杂注或使用[/fp：精确](../build/reference/fp-specify-floating-point-behavior.md)或[/fp： strict](../build/reference/fp-specify-floating-point-behavior.md)编译器选项来启用精确语义。 如果没有指定其他浮点命令行选项，编译器将默认为 **/fp：精确**。

- 设置**fenv_access （on）** 时，不能使用**float_control**禁用精确语义。

**Fenv_access**的各种优化类型为：

- 全局公共子表达式消除

- 代码运动

- 常量折叠

其他浮点杂注包括：

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>示例

此示例将**fenv_access**设置为**on** ，以设置24位精度的浮点控制寄存器：

```cpp
// pragma_directive_fenv_access_x86.cpp
// compile with: /O2 /arch:IA32
// processor: x86
#include <stdio.h>
#include <float.h>
#include <errno.h>
#pragma fenv_access (on)

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=9.999999776482582e-03
```

如果注释掉上一示例中的 `#pragma fenv_access (on)`，则输出将有所不同。 这是因为编译器执行编译时计算，这不会使用控件模式。

```cpp
// pragma_directive_fenv_access_2.cpp
// compile with: /O2 /arch:IA32
#include <stdio.h>
#include <float.h>

int main() {
   double z, b = 0.1, t = 0.1;
   unsigned int currentControl;
   errno_t err;

   err = _controlfp_s(&currentControl, _PC_24, _MCW_PC);
   if (err != 0) {
      printf_s("The function _controlfp_s failed!\n");
      return -1;
   }
   z = b * t;
   printf_s ("out=%.15e\n",z);
}
```

```Output
out=1.000000000000000e-02
```

## <a name="see-also"></a>另请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
