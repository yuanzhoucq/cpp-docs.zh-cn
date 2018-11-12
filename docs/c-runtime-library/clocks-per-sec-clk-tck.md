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
ms.openlocfilehash: 40401028ef16f0d46baec92a37b2ba422d1e56ae
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50621346"
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