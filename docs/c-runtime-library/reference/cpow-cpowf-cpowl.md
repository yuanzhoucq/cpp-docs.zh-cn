---
title: cpow、cpowf、cpowl | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp
- devlang-cpp
ms.topic: reference
apiname:
- cpow
- cpowf
- cpowl
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
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- cpow
- cpowf
- cpowl
- complex/cpow
- complex/cpowf
- complex/copwl
dev_langs:
- C++
helpviewer_keywords:
- cpow function
- cpowf function
- complex/cpowl function
ms.assetid: 83fe2187-22b7-4295-ab16-4d77abdbb80b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8311b4c8bd8c082b03f01a2df253c55d170c560e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32394777"
---
# <a name="cpow-cpowf-cpowl"></a>cpow、cpowf、cpowl

检索某个数字的指定次幂的值，其中基数和指数为复数。 此函数具有沿负实轴的指数分支切割。

## <a name="syntax"></a>语法

```C
_Dcomplex cpow(
   _Dcomplex x, _Dcomplex y
);
_Fcomplex cpow(
   _Fcomplex x, _Fcomplex y
);  // C++ only
_Lcomplex cpow(
   _Lcomplex x, _Lcomplex y
);  // C++ only
_Fcomplex cpowf(
   _Fcomplex x, _Fcomplex y
);
_Lcomplex cpowl(
   _Lcomplex x, _Lcomplex y
);
```

### <a name="parameters"></a>参数

*x*<br/>
基数。

*y*<br/>
指数。

## <a name="return-value"></a>返回值

值*x*的幂*y*与剪切的分支*x*负实际轴。

## <a name="remarks"></a>备注

由于 c + + 允许重载，你可以调用的重载**cpow**采用并返回 **_Fcomplex**和 **_Lcomplex**值。 在 C 程序中， **cpow**始终采用并返回 **_Dcomplex**值。

## <a name="requirements"></a>要求

|例程|C 标头|C++ 标头|
|-------------|--------------|------------------|
|**cpow**， **cpowf**， **cpowl**|\<complex.h>|\<ccomplex>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[按字母顺序的函数参考](crt-alphabetical-function-reference.md)<br/>
[cexp、cexpf、cexpl](cexp-cexpf-cexpl.md)<br/>
[clog10、clog10f、clog10l](clog10-clog10f-clog10l.md)<br/>
[clog、clogf、clogl](clog-clogf-clogl.md)<br/>
