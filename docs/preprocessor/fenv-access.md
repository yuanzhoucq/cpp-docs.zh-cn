---
title: fenv_access 杂注
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.fenv_access
- fenv_access_CPP
helpviewer_keywords:
- pragmas, fenv_access
- fenv_access pragma
ms.assetid: 2ccea292-0ae4-42ce-9c67-cc189299857b
ms.openlocfilehash: c8e66881bde12df28bf24e18230471cb4caca792
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218608"
---
# <a name="fenv_access-pragma"></a>fenv_access 杂注

禁用 (**启用**) 或启用 (**关闭**) 可更改浮点环境标志测试和模式更改的优化。

## <a name="syntax"></a>语法

> **#pragma fenv_access (** { **on** | **off** } **)**

## <a name="remarks"></a>备注

默认情况下, **fenv_access**为**off**。 如果编译器可以假设您的代码不能访问或操作浮点环境, 则它可以执行很多浮点代码优化。 将**fenv_access**设置为 **"开"** 可通知编译器: 代码访问浮点环境以测试状态标志和异常, 或设置控制模式标志。 编译器将禁用这些优化, 以便您的代码可以一致地访问浮点环境。

有关浮点行为的详细信息, 请参阅[/fp (指定浮点行为)](../build/reference/fp-specify-floating-point-behavior.md)。

受**fenv_access**限制的各种优化类型为:

- 全局公共子表达式消除

- 代码运动

- 常量折叠

其他浮点杂注包括：

- [float_control](../preprocessor/float-control.md)

- [fp_contract](../preprocessor/fp-contract.md)

## <a name="examples"></a>示例

此示例将**fenv_access**设置为**on** , 以设置24位精度的浮点控制寄存器:

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

如果从前面的`#pragma fenv_access (on)`示例中注释掉, 则输出不同, 因为编译器执行编译时计算, 而该计算不使用控件模式。

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

## <a name="see-also"></a>请参阅

[Pragma 指令和 __pragma 关键字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
