---
title: 在 __asm 块中访问 C 或 C++ 数据
ms.date: 08/30/2018
helpviewer_keywords:
- data members [C++], in __asm blocks
- data access [C++], in __asm blocks
- __asm keyword [C++], data members
- structure types in __asm blocks
ms.assetid: e99f5a28-0381-4090-8ece-6af8f2436a49
ms.openlocfilehash: b4341f87226118906749dcdb18b9227e68be6a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318081"
---
# <a name="accessing-c-or-c-data-in-__asm-blocks"></a>在 __asm 块中访问 C 或 C++ 数据

**微软特定**

内联程序集的一个重大便利就是能够按名称引用 C 或 C++ 变量。 `__asm` 块可引用任何符号，包括位于块所在的范围内的变量名称。 例如，如果 C 变量 `var` 位于范围内，则指令

```cpp
__asm mov eax, var
```

在 EAX 中存储 `var` 的值。

如果类、结构或联合成员具有唯一名称，`__asm`则块只能使用成员名称引用它，而不指定句点 （**.**）`typedef`运算符之前的变量或名称。 但是，如果成员名称不是唯一的，则必须在紧靠句点运算符前面放置变量或 `typedef` 名称。 例如，以下示例中的结构共享 `same_name` 作为其成员名称：

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

**结束微软特定**

## <a name="see-also"></a>另请参阅

[在 __asm 块中使用 C 或 C++](../../assembler/inline/using-c-or-cpp-in-asm-blocks.md)<br/>
