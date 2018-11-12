---
title: __setusermatherr
ms.date: 11/04/2016
apiname:
- __setusermatherr
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr100.dll
- api-ms-win-crt-math-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- __setusermatherr
helpviewer_keywords:
- __setusermatherr
ms.assetid: f306818d-381a-4d68-8739-71b92bacb5ea
ms.openlocfilehash: 116abd203cc289c63535a8e41a005a6fd248b08b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640461"
---
# <a name="setusermatherr"></a>__setusermatherr

指定用户提供的例程（而不是 [_matherr](../c-runtime-library/reference/matherr.md) 例程）处理数学错误。

## <a name="syntax"></a>语法

```cpp
void __setusermatherr(
   _HANDLE_MATH_ERROR pf
   )
```

#### <a name="parameters"></a>参数

*pf*<br/>
指向用户提供的 `_matherr` 的实现的指针。

将 *pf* 参数的类型声明为 `typedef int (__cdecl * _HANDLE_MATH_ERROR)(struct _exception *)`。

## <a name="remarks"></a>备注

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|__setusermatherr|matherr.c|