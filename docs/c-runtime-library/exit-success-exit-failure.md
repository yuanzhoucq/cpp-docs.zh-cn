---
title: EXIT_SUCCESS、EXIT_FAILURE
ms.date: 06/25/2018
f1_keywords:
- EXIT_FAILURE
- EXIT_SUCCESS
helpviewer_keywords:
- EXIT_SUCCESS constant
- EXIT_FAILURE constant
ms.assetid: ff2c82cb-c0bb-4556-a812-59aa278bfac5
ms.openlocfilehash: 562c97b62840285719344d124d8df9944bec25cb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519166"
---
# <a name="exitsuccess-exitfailure"></a>EXIT_SUCCESS、EXIT_FAILURE

## <a name="required-header"></a>必需的标头

```c
#include <stdlib.h>
```

## <a name="remarks"></a>备注

这些是 [exit](reference/exit-exit-exit.md) 和 [_exit](reference/exit-exit-exit.md) 函数的参数以及 [atexit](reference/atexit.md) 和 [_onexit](reference/onexit-onexit-m.md) 函数的返回值。

|返回的常量|已定义的值|
|-|-|
|EXIT_SUCCESS|0|
|EXIT_FAILURE|1|

## <a name="see-also"></a>请参阅

[全局常量](../c-runtime-library/global-constants.md)
