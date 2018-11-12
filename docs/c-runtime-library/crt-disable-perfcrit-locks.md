---
title: _CRT_DISABLE_PERFCRIT_LOCKS
ms.date: 11/04/2016
f1_keywords:
- _CRT_DISABLE_PERFCRIT_LOCKS
- CRT_DISABLE_PERFCRIT_LOCKS
helpviewer_keywords:
- CRT_DISABLE_PERFCRIT_LOCKS constant
- _CRT_DISABLE_PERFCRIT_LOCKS constant
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
ms.openlocfilehash: 475cc57b5b47f5abf8c268db3acf9e727ce6a743
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50593451"
---
# <a name="crtdisableperfcritlocks"></a>_CRT_DISABLE_PERFCRIT_LOCKS

在 I/O 操作中禁用性能关键锁定。

## <a name="syntax"></a>语法

```
#define _CRT_DISABLE_PERFCRIT_LOCKS
```

## <a name="remarks"></a>备注

定义此符号可通过强制所有 I/O 操作采用单线程 I/O 模型，来提高单线程 I/O 绑定程序的性能。 有关详细信息，请参阅[多线程库性能](../c-runtime-library/multithreaded-libraries-performance.md)。

## <a name="see-also"></a>请参阅

[全局常量](../c-runtime-library/global-constants.md)