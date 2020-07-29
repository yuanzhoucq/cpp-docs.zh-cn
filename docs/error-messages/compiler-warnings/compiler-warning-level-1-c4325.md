---
title: 编译器警告（等级 1）C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: 551680bc1d24097200a1e641bc4238f883ad94dd
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230696"
---
# <a name="compiler-warning-level-1-c4325"></a>编译器警告（等级 1）C4325

> 已忽略标准节 "*section*" 的属性

## <a name="remarks"></a>备注

不能更改标准节的属性。 例如：

```cpp
#pragma section(".sdata", long)
```

这会覆盖使用数据类型的 `.sdata` 数据类型的标准部分 **`short`** **`long`** 。

不能更改其属性的标准部分包括、

- 。数据

- .sdata

- bss

- 。 .sbss

- .text

- . const

- .sconst

- 。 rdata

- .srdata

稍后可能会添加其他部分。

## <a name="see-also"></a>另请参阅

[区](../../preprocessor/section.md)
