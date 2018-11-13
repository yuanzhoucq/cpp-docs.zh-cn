---
title: HUGE_VAL、_HUGE
ms.date: 11/04/2016
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 8f8342990ea62b368b46ed56f0697a844c755a61
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/10/2018
ms.locfileid: "51522124"
---
# <a name="hugeval-huge"></a>HUGE_VAL、_HUGE

## <a name="syntax"></a>语法

```

#include <math.h>
```

## <a name="remarks"></a>备注

`HUGE_VAL` 是可表示的最大双精度值。 在出现错误时，该值将由许多运行时数学函数返回。 对于某些函数，将返回 -`HUGE_VAL`。 `HUGE_VAL` 定义为 `_HUGE`，而运行时数学函数返回 `HUGE_VAL`。 为确保一致性，还应在代码中使用 `HUGE_VAL`。

## <a name="see-also"></a>请参阅

[全局常量](../c-runtime-library/global-constants.md)