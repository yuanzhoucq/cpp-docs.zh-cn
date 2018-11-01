---
title: 名称修饰
ms.date: 09/05/2018
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: c01e684be62dbb8716f8556680b1c692af1efc45
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50598856"
---
# <a name="name-decoration"></a>名称修饰

名称修饰通常是指 C++ 命名约定，但也可应用于多个 C 情形。 默认情况下，C++ 使用函数名、参数和返回类型来为该函数创建链接器名称。 考虑以下函数：

```
void CALLTYPE test(void)
```

下表显示了各种调用约定的链接器名称。

|调用约定|外部“C”或 .c 文件|.cpp、.cxx 或 /TP|
|------------------------|---------------------------|------------------------|
|C 命名约定 (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|Fastcall 命名约定 (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|标准调用命名约定 (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|Vectorcall 命名约定 (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

使用外部“C”从 C++ 调用 C 函数。 外部“C”对非类 C++ 函数强制使用 C 命名约定。 请注意编译器开关 **/Tc**或 **/Tp**，它们通知编译器忽略文件扩展名并分别将文件编译为 C 或 c + +。 这些选项可能会导致期望外的名称。

具有不匹配的参数的函数原型也会导致此错误。 名称修饰将函数的参数合并到最终修饰的函数名中。 调用的函数具有与函数声明中不匹配的参数类型时也可能导致 LNK2001。

目前，在编译器供应商之间，甚至在同一编译器的不同版本之间尚不存在 C++ 命名标准。 因此，链接用其他编译器编译的对象文件可能不会产生相同的命名方案，从而导致无法解析的外部对象。

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)