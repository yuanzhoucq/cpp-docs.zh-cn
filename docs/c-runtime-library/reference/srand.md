---
title: "srand | Microsoft 文档"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: srand
apilocation:
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
apitype: DLLExport
f1_keywords: srand
dev_langs: C++
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
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 205dcb2ba7d61dff1286fd926e3f10cf2a162e9a
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/05/2018
---
# <a name="srand"></a>srand

设置使用的伪随机数字生成器的起始种子值`rand`函数。

## <a name="syntax"></a>语法

```C
void srand(
   unsigned int seed
);
```

### <a name="parameters"></a>参数

*种子*  
伪随机数生成的种子

## <a name="remarks"></a>备注

`srand` 函数在当前线程中设置生成一系列伪随机整数的起点。 若要重新初始化生成器来创建相同的结果序列，调用`srand`函数，并使用相同*种子*再次自变量。 任何其他值*种子*到伪随机序列中的不同起始点设置的生成器。 `rand` 检索生成的伪随机数。 调用`rand`对任何调用之前`srand`生成相同的序列与调用`srand`与*种子*传递为 1。

## <a name="requirements"></a>惠?

|例程所返回的值|必需的标头|
|-------------|---------------------|
|`srand`|\<stdlib.h>|

有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。

## <a name="example"></a>示例

请参阅 [rand](../../c-runtime-library/reference/rand.md) 的示例。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)  
[rand](../../c-runtime-library/reference/rand.md)  
