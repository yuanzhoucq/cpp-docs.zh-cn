---
title: 在 __asm 块中访问 C 或 C++ 数据
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: 8fbe855c2f5de96d81e6c8a27c4bfcee0864f12c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193037"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>在 __asm 块中访问 C 或 C++ 数据

**Microsoft 专用**

内联程序集的一个重大便利就是能够按名称引用 C 或 C++ 变量。 **`__asm`** 块可以引用在块出现的范围内的任何符号，包括变量名称。 例如，如果 C 变量 `var` 位于范围内，则指令

```cpp
__asm mov eax, var
```

在 EAX 中存储 `var` 的值。

如果类、结构或联合成员具有唯一的名称， **`__asm`** 块只能使用成员名称来引用它，而无需在 **`typedef`** 句点（**.**）运算符前面指定变量或名称。 但是，如果成员名称不唯一，则必须将变量或 **`typedef`** 名称紧靠在 period 运算符之前。 例如，以下示例中的结构共享 `same_name` 作为其成员名称：

如果使用以下类型声明变量

```cpp
struct first_type hal;
struct second_type oat;
```

对成员 `same_name` 的所有引用都必须使用变量名称，因为 `same_name` 不是唯一的。 但成员 `weasel` 具有唯一的名称，因此您可以只使用其成员名称来引用它：

```cpp
// InlineAssembler_Accessing_C_asm_Blocks.cpp
// processor: x86
#include <stdio.h>
struct first_type
{
   char *weasel;
   int same_name;
};

struct second_type
{
   int wonton;
   long same_name;
};

int main()
{
   struct first_type hal;
   struct second_type oat;

   __asm
   {
      lea ebx, hal
      mov ecx, [ebx]hal.same_name ; Must use 'hal'
      mov esi, [ebx].weasel       ; Can omit 'hal'
   }
   return 0;
}
```

请注意，省略变量名只是为了方便编码。 无论变量名是否存在，都会生成相同的程序集指令。

您可以在 C++ 中访问数据成员而无需考虑访问限制。 但是，您无法调用成员函数。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[在 __asm 块中使用 C 或 c + +](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
