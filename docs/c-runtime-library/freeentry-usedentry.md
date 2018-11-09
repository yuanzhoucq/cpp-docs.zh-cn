---
title: _FREEENTRY、_USEDENTRY
ms.date: 11/04/2016
f1_keywords:
- USEDENTRY
- _USEDENTRY
- _FREEENTRY
- FREEENTRY
helpviewer_keywords:
- _USEDENTRY constant
- _FREEENTRY constant
- FREEENTRY constant
- USEDENTRY constant
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
ms.openlocfilehash: 3bf05807930373a905a5bf71cf4ebc1f119056a2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50513979"
---
# <a name="freeentry-usedentry"></a>_FREEENTRY、_USEDENTRY

## <a name="syntax"></a>语法

```
#include <malloc.h>
```

## <a name="remarks"></a>备注

这些常量表示由 `_heapwalk` 例程分配给 _HEAPINFO 结构的 _useflag 元素的值。 它们指示堆条目的状态。

## <a name="see-also"></a>请参阅

[_heapwalk](../c-runtime-library/reference/heapwalk.md)<br/>
[全局常量](../c-runtime-library/global-constants.md)