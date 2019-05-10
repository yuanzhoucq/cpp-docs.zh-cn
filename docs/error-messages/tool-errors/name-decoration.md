---
title: 名称修饰
ms.date: 04/22/2019
helpviewer_keywords:
- name decoration [C++]
- names [C++], decorated
- decorated names, calling conventions
ms.assetid: 8327a27b-bb4f-49f2-8218-b851b9d2a463
ms.openlocfilehash: d1557f53a07a544ff4f9e5a63f905e6854fb74ce
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857173"
---
# <a name="name-decoration"></a>名称修饰

名称修饰通常是指 C++ 命名约定，但也可应用于多个 C 情形。 默认情况下，C++ 使用函数名、参数和返回类型来为该函数创建链接器名称。 请考虑以下函数声明：

`void CALLTYPE test(void);`

下表显示了各种调用约定的链接器名称。

|调用约定|`extern "C"` 或`.c`文件|`.cpp``.cxx`或 `/TP`|
|------------------------|---------------------------|------------------------|
|C 命名约定 (`__cdecl`)|`_test`|`?test@@ZAXXZ`|
|快速调用命名约定 (`__fastcall`)|`@test@0`|`?test@@YIXXZ`|
|标准调用命名约定 (`__stdcall`)|`_test@0`|`?test@@YGXXZ`|
|矢量调用命名约定 (`__vectorcall`)|`test@@0`|`?test@@YQXXZ`|

使用`extern "C"`调用 C 函数从C++。 `extern "C"` 强制对非类 C 命名约定使用C++函数。 请注意编译器开关 **/Tc**或 **/Tp**，它们通知编译器忽略文件扩展名和文件编译为 C 或C++分别。 这些选项可能会导致不希望链接器名称。

具有不匹配的参数的函数原型也会导致此错误。 名称修饰将函数的参数合并到最终修饰的函数名中。 调用的函数具有不匹配函数声明中的参数类型也可能导致 LNK2001。

目前没有用于标准C++命名编译器供应商之间、 甚至之间不同版本的编译器。 链接的其他编译器编译的对象文件可能不会产生相同的命名方案，并可能导致无法解析的外部。

## <a name="see-also"></a>请参阅

[链接器工具错误 LNK2001](../../error-messages/tool-errors/linker-tools-error-lnk2001.md)