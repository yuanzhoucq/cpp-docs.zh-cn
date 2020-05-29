---
title: C 调整了大小的整型
ms.date: 11/04/2016
helpviewer_keywords:
- sized integer types
ms.assetid: 0d6199b4-d0ab-4e8c-a769-785f5afb92eb
ms.openlocfilehash: 136065466d3adb4017cf18f2baf8c3387ffbd035
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62313293"
---
# <a name="c-sized-integer-types"></a>C 调整了大小的整型

**Microsoft 专用**

Microsoft C 支持固定大小整数类型。 可以使用 __intn 类型说明符声明 8 位、16 位、32 位或 64 位整数变量，其中 n 是整数变量的大小（以位为单位）   。 n 的值可以是 8、16、32 或 64  。 以下示例为四种类型的固定大小整数各声明了一个变量：

```
__int8 nSmall;      // Declares 8-bit integer
__int16 nMedium;    // Declares 16-bit integer
__int32 nLarge;     // Declares 32-bit integer
__int64 nHuge;      // Declares 64-bit integer
```

固定大小整数的前三种类型是大小相同的 ANSI 类型的同义词，用于编写在多个平台中具有相同的行为的可移植代码。 请注意，__int8 数据类型与 char 类型是同义词，\__int16 与 short 类型是同义词，\__int32 与 int 类型是同义词。\__int64 类型没有等效的 ANSI 匹配项。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[基本类型的存储](../c-language/storage-of-basic-types.md)
