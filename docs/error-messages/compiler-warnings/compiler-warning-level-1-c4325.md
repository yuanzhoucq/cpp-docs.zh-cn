---
title: 编译器警告（等级 1）C4325
ms.date: 08/27/2018
f1_keywords:
- C4325
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
ms.openlocfilehash: e0a13761b0657d054065358994638779817dad6a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/24/2020
ms.locfileid: "80163019"
---
# <a name="compiler-warning-level-1-c4325"></a>编译器警告（等级 1）C4325

> 已忽略标准节 "*section*" 的属性

## <a name="remarks"></a>备注

不能更改标准节的属性。 例如：

```cpp
#pragma section(".sdata", long)
```

这会覆盖使用**long**数据类型的**short**数据类型 `.sdata` 标准部分。

不能更改其属性的标准部分包括、

- 。数据

- .sdata

- .bss

- .sbss

- .text

- .const

- .sconst

- 。 rdata

- .srdata

稍后可能会添加其他部分。

## <a name="see-also"></a>另请参阅

[部分](../../preprocessor/section.md)
