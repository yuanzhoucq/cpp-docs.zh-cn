---
title: CLOCKS_PER_SEC、CLK_TCK
ms.date: 11/04/2016
f1_keywords:
- CLOCKS_PER_SEC
- CLK_TCK
helpviewer_keywords:
- CLOCKS_PER_SEC
- CLK_TCK constant
ms.assetid: bc285106-383d-44cb-91bf-276ad7de57bf
ms.openlocfilehash: a604425809f43be238cbcc7b9148782bb937e00f
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220356"
---
# <a name="clockspersec-clktck"></a>CLOCKS_PER_SEC、CLK_TCK

## <a name="syntax"></a>语法

```
#include <time.h>
```

## <a name="remarks"></a>备注

时间（以秒为单位）是由 `clock` 函数返回的值除以 `CLOCKS_PER_SEC` 所得的值。 `CLK_TCK` 是等效的，但被视为已过时。

## <a name="see-also"></a>请参阅

[clock](../c-runtime-library/reference/clock.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)
