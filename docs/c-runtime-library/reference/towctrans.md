---
title: towctrans
ms.date: 11/04/2016
apiname:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: b814c65d2f5d0bb18b19d97a539d79dd6df8a1c6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561403"
---
# <a name="towctrans"></a>towctrans

转换字符。

## <a name="syntax"></a>语法

```C
wint_t towctrans(
   wint_t c,
   wctrans_t category
);
```

### <a name="parameters"></a>参数

*c*<br/>
要转换的字符。

*category*<br/>
包含 [wctrans](wctrans.md) 的返回值的标识符。

## <a name="return-value"></a>返回值

字符*c*后面**towctrans**使用中的转换规则*类别*。

## <a name="remarks"></a>备注

值*类别*必须对之前成功调用返回[wctrans](wctrans.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**towctrans**|\<wctype.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

请参阅**wctrans**有关的示例，使用**towctrans**。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
