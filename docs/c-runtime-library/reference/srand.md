---
title: srand
ms.date: 4/2/2020
api_name:
- srand
- _o_srand
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-utility-l1-1-0.dll
- ntoskrnl.exe
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- srand
helpviewer_keywords:
- random starting point
- random starting point, setting
- random numbers, generating
- srand function
- numbers, pseudorandom
- numbers, random
- pseudorandom numbers
- starting points, setting random
- starting points
ms.openlocfilehash: a8d018d429b2a484f88b7c1e0679f1f799983910
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81355486"
---
# <a name="srand"></a>srand

设置**兰特**函数使用的伪随机数生成器的起始种子值。

## <a name="syntax"></a>语法

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>参数

seed**<br/>
伪随机数生成的种子

## <a name="remarks"></a>备注

**srand**函数设置在当前线程中生成一系列伪随机整数的起点。 要重新初始化生成器以创建相同的结果序列，请调用**srand**函数并再次使用相同的*种子*参数。 *种子的*任何其他值将生成器设置到伪随机序列中不同的起始点。 **rand**检索生成的伪随机数。 对**srand**的任何调用之前调用**rand**将生成与调用**srand**相同的序列，*种子*传递为 1。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**srand**|\<stdlib.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅 [rand](rand.md) 的示例。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[兰德](rand.md)<br/>
