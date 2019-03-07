---
title: int 类型
ms.date: 11/04/2016
helpviewer_keywords:
- int data type
- type int
- portability [C++], type int
- signed integers
ms.assetid: 0067ce9a-281e-491a-ae63-632952981e13
ms.openlocfilehash: 848c9799e7ab5cfdfd2b25cc84e55de02c673f3e
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150007"
---
# <a name="type-int"></a>int 类型

带符号或无符号的 `int` 项的大小是特定计算机上的一个整数的标准大小。 例如，在 16 位操作系统中，`int` 类型通常是 16 位（或 2 字节）。 在 32 位操作系统中，`int` 类型通常是 32 位（或 4 字节）。 因此，`int` 类型与 `short int` 或 long int 类型等效，`unsigned int` 类型与 unsigned short 或 `unsigned long` 类型等效，具体取决于目标环境。 除非另有规定，否则所有 `int` 类型都表示带符号值。

类型说明符 `int` 和 `unsigned int`（或简写为 `unsigned`）定义 C 语言的某些功能（例如，`enum` 类型）。 在这些情况下，`int` 的定义和特定实现的 unsigned int 决定实际存储。

**Microsoft 专用**

带符号整数以 2 的补数的形式表示。 最高有效位保留符号：1 表示负数，0 表示正数和零。 值的范围在 [C++ 整数限制](../c-language/cpp-integer-limits.md)中给定（摘自 LIMITS.H 头文件）。

**结束 Microsoft 专用**

> [!NOTE]
>  int 和 unsigned int 类型说明符在 C 程序中的使用很广泛，因为这些类型允许特定计算机以对自己最有效的方式处理整数值。 但是，由于 int 和 unsigned int 类型的大小不同，依赖于特定 int 大小的程序不能移植到其他计算机。 若要使程序更易于移植，则可以使用带 sizeof 运算符（如 [sizeof 运算符](../c-language/sizeof-operator-c.md)中所讨论的）的表达式，而不是具有硬编码数据大小的表达式。

## <a name="see-also"></a>请参阅

[基本类型的存储](../c-language/storage-of-basic-types.md)
