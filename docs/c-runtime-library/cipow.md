---
title: _CIpow
ms.date: 11/04/2016
apiname:
- _CIpow
apilocation:
- msvcr100.dll
- msvcr110.dll
- msvcr120.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- CIpow
- _CIpow
helpviewer_keywords:
- CIpow intrinsic
- _CIpow intrinsic
ms.assetid: 477aaf0c-ac58-4252-89dd-9f3e35d47536
ms.openlocfilehash: 5e41e44096bb353f95dd725f5ad64e95702f330f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50517866"
---
# <a name="cipow"></a>_CIpow

基于堆栈中的顶部值，计算提升到 *y* 电源的 *x*。

## <a name="syntax"></a>语法

```
void __cdecl _CIpow();
```

## <a name="remarks"></a>备注

此版本的 `pow` 函数具有编译器理解的专用化调用约定。 它将加快执行的速度，因为它可防止生成副本和帮助注册表分配。

生成的值被将被推送到堆栈顶部。

## <a name="requirements"></a>要求

**平台：** x86

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](../c-runtime-library/reference/crt-alphabetical-function-reference.md)<br/>
[pow、powf、powl](../c-runtime-library/reference/pow-powf-powl.md)