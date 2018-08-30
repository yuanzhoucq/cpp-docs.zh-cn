---
title: 编译器警告 （等级 1） C4325 |Microsoft Docs
ms.custom: ''
ms.date: 08/27/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4325
dev_langs:
- C++
helpviewer_keywords:
- C4325
ms.assetid: 8127a08c-d626-481b-aa7b-04a3fdc9a9ec
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd265938afb51cc402dc84f38b7e95188c6292a7
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43197480"
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