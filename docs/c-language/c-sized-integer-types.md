---
title: C 调整了大小的整型
ms.date: 07/22/2020
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 7f785efb2fc93d2ec57783dd20a43642c87e4a4c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87226498"
---
# <a name="c-sized-integer-types"></a>C 调整了大小的整型

**Microsoft 专用**

Microsoft C 支持固定大小整数类型。 可以使用 `__intN` 类型说明符声明 8 位、16 位、32 位或 64 位整型变量，其中 `N` 是整型变量的大小（以位为单位）。 n 的值可以是 8、16、32 或 64  。 以下示例为四种类型的固定大小整数各声明了一个变量：

```C
__int8  nSmall;     // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

前三种类型的大小整数与有相同大小的 ANSI 类型同义。 它们对于编写跨多个平台具有完全相同行为的可移植代码非常有用。 `__int8` 数据类型与 `char` 类型同义，`__int16` 与 `short` 类型同义，`__int32` 与 `int` 类型同义，`__int64` 与 `long long` 类型同义。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[基本类型的存储](../c-language/storage-of-basic-types.md)
