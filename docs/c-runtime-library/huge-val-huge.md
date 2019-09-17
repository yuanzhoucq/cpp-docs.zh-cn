---
title: HUGE_VAL、_HUGE
ms.date: 11/04/2016
api_name:
- _HUGE
api_location:
- msvcrt.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _HUGE
- HUGE_VAL
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
ms.openlocfilehash: 3a0469b7158e765b1b1c6f34cb01c0e90beb1401
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70940264"
---
# <a name="huge_val-_huge"></a>HUGE_VAL、_HUGE

## <a name="syntax"></a>语法

```
#include <math.h>
```

## <a name="remarks"></a>备注

`HUGE_VAL` 是可表示的最大双精度值。 在出现错误时，该值将由许多运行时数学函数返回。 对于某些函数，将返回 -`HUGE_VAL`。 `HUGE_VAL` 定义为 `_HUGE`，而运行时数学函数返回 `HUGE_VAL`。 为确保一致性，还应在代码中使用 `HUGE_VAL`。

## <a name="see-also"></a>请参阅

[全局常量](../c-runtime-library/global-constants.md)
