---
title: _FREEENTRY、_USEDENTRY | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- USEDENTRY
- _USEDENTRY
- _FREEENTRY
- FREEENTRY
dev_langs:
- C++
helpviewer_keywords:
- _USEDENTRY constant
- _FREEENTRY constant
- FREEENTRY constant
- USEDENTRY constant
ms.assetid: 26f658e6-6846-4a4e-9984-262cfe392770
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 60487a502fd304be39f973659cb5fd3432ec7a1d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096790"
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