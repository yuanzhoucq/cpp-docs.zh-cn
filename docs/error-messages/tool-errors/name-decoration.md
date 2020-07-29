---
title: 名称修饰
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: 6a43b952b2f8f9bcbb5e835bf8e20682c99f2935
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218034"
---
# <a name="name-decoration"></a>名称修饰

名称修饰通常是指 C++ 命名约定，但也可应用于多个 C 情形。 默认情况下，C++ 使用函数名、参数和返回类型来为该函数创建链接器名称。 请考虑以下函数声明：

`void CALLTYPE test(void);`

下表显示了各种调用约定的链接器名称。

|调用约定|`extern "C"`或 `.c` 文件|`.cpp`， `.cxx` 或`/TP`|
|------------------------|---------------------------|------------------------|
|C 命名约定（ **`__cdecl`** ）|`_test`|`?test@@ZAXXZ`|
|快速调用命名约定（ **`__fastcall`** ）|`@test@0`|`?test@@YIXXZ`|
|标准调用命名约定（ **`__stdcall`** ）|`_test@0`|`?test@@YGXXZ`|
|向量调用命名约定（ **`__vectorcall`** ）|`test@@0`|`?test@@YQXXZ`|

使用 `extern "C"` 调用 c + + 中的 c 函数。 `extern "C"`强制对非类 c + + 函数使用 C 命名约定。 请注意编译器开关 **/tc**或 **/tp**，这会告诉编译器忽略文件扩展名，并分别将文件编译为 C 或 c + +。 这些选项可能会导致不需要的链接器名称。

具有不匹配的参数的函数原型也会导致此错误。 名称修饰将函数的参数合并到最终修饰的函数名中。 使用与函数声明中的参数类型不匹配的参数类型调用函数也可能导致 LNK2001。

在编译器供应商之间，甚至在不同版本的编译器之间，c + + 命名均不提供标准。 链接由其他编译器编译的对象文件可能不会生成相同的命名方案，并且可能会导致无法解析的外部对象。

## <a name="see-also"></a>另请参阅

[链接器工具错误 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)
