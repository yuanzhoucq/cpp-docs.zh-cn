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
ms.openlocfilehash: eef065ac4fcedf13f3a5d54d4df0563fd04ef965
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/11/2019
ms.locfileid: "57750671"
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
