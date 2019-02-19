---
title: 结构成员的填充和对齐
ms.date: 10/18/2018
helpviewer_keywords:
- structure members, padding and alignment
ms.assetid: c999820b-dd47-41fc-b923-e4c7ebbcd30f
ms.openlocfilehash: 0f9c70ed074a11800b707aa48ec8e0e2f8b4f999
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148109"
---
# <a name="padding-and-alignment-of-structure-members"></a>结构成员的填充和对齐

**ANSI 3.5.2.1** 结构的成员的填充和对齐方式，以及位域是否可以跨存储单元边界

结构成员按其声明顺序进行存储：第一个成员的内存地址最低，最后一个成员的内存地址最高。

每个数据对象具有 alignment-requirement。 所有数据（结构、联合和数组除外）的对齐要求是对象的大小或当前打包大小（使用 /Zp 或 `pack` 杂注指定，以较小者为准）。 对于结构、联合和数组，对齐要求是其成员的最大对齐要求。 为每个对象分配一个 offset，以便

*offset* **%** *alignment-requirement* **== 0**

如果整型的大小相同，并且下一个位域适合当前分配单元而未跨位域的常见对齐需求所强加的边界，则将相邻位域打包到相同的 1 字节、2 字节或 4 字节分配单元中。

## <a name="see-also"></a>请参阅

[结构、联合、枚举和位域](../c-language/structures-unions-enumerations-and-bit-fields.md)
