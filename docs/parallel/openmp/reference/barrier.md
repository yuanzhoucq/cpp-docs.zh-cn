---
title: 屏障 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c220106d62bf65505c9c5b48085a9ee3e67fe0cb
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415026"
---
# <a name="barrier"></a>barrier

同步团队; 中的所有线程所有线程在屏障，都暂停，直到所有线程都执行屏障。

## <a name="syntax"></a>语法

```
#pragma omp barrier
```

## <a name="remarks"></a>备注

`barrier`指令支持任何 OpenMP 子句。

有关详细信息，请参阅[2.6.3 barrier 指令](../../../parallel/openmp/2-6-3-barrier-directive.md)。

## <a name="example"></a>示例

有关如何使用的示例`barrier`，请参阅[主](../../../parallel/openmp/reference/master.md)。

## <a name="see-also"></a>请参阅

[指令](../../../parallel/openmp/reference/openmp-directives.md)