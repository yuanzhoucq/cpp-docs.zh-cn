---
title: 编译器警告（等级 1）C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 293cbbcfe134f6cb4f5e1bf924be7c03fa278833
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50492582"
---
# <a name="compiler-warning-level-1-c4325"></a>编译器警告（等级 1）C4325

> 忽略标准节*部分*被忽略

## <a name="remarks"></a>备注

您不能更改标准节的特性。 例如：

```cpp
#pragma section(".sdata", long)
```

这会覆盖`.sdata`使用标准节**短**数据类型为**长**数据类型。

标准节您不能更改其属性包括：

- .data

- .sdata

- .bss

- .sbss

- .text

- .const

- .sconst

- .rdata

- .srdata

可能在以后添加其他部分。

## <a name="see-also"></a>请参阅

[section](../../preprocessor/section.md)