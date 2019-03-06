---
title: Visual C++ 64 位迁移的常见问题
ms.date: 11/04/2016
helpviewer_keywords:
- 64-bit programming [C++], migration
- 64-bit compiler [C++], migration
- porting 32-bit code to 64-bit code
- upgrading Visual C++ applications, 32-bit code
- migration [C++], 64-bit code issues
- 32-bit code porting [C++]
- 64-bit applications [C++]
- 64-bit compiler [C++], porting 32-bit code
- Win64 [C++]
ms.assetid: d17fb838-7513-4e2d-8b27-a1666f17ad76
ms.openlocfilehash: c74766c86048f6dd7358d16b8d5d1f2b493450c1
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57414416"
---
# <a name="common-visual-c-64-bit-migration-issues"></a>Visual C++ 64 位迁移的常见问题

用 Visual C++ 创建在 64 位 Windows 操作系统中运行的应用程序时，应注意以下问题：

- 在 64 位 Windows 操作系统中，`int` 和 `long` 是 32 位值。 对于计划为 64 位平台编译的程序，应注意不要将指针赋给 32 位变量。 在 64 位平台上，指针为 64 位，如果将该指针赋给 32 位变量，则将截断该指针值。

- `size_t``time_t`，和`ptrdiff_t`是 64 位 Windows 操作系统上的 64 位值。

- 在 Visual C++ 2005 之前的 Visual C++ 版本中，`time_t` 在 32 位 Windows 操作系统中是 32 位值。 默认情况下，`time_t` 现在为 64 位整数。 有关详细信息，请参阅[时间管理](../c-runtime-library/time-management.md)。

   应注意代码在哪里采用 `int` 值并将其作为 `size_t` 或 `time_t` 值处理。 数字有可能增长得比 32 位数大，并且数据在被传递回 `int` 存储时将被截断。

在 64 位 Windows 操作系统中，%X（十六进制 `int` 格式）`printf` 修饰符将不会按预期方式工作。 它将只对传递给它的值的前 32 位值执行操作。

- 使用 %I32x，以十六进制格式显示 32 位整数类型。

- 使用 %I64x，以十六进制格式显示 64 位整数类型。

- 在 64 位 Windows 操作系统中，%p（指针的十六进制格式）将按预期方式工作。

有关详细信息，请参见:

- [编译器选项](../build/reference/compiler-options.md)

- [迁移提示](/windows/desktop/WinProg64/migration-tips)

## <a name="see-also"></a>请参阅

[针对 64 位 x64 目标配置 Visual C++](../build/configuring-programs-for-64-bit-visual-cpp.md)<br/>
[Visual C++ 移植和升级指南](../porting/visual-cpp-porting-and-upgrading-guide.md)
