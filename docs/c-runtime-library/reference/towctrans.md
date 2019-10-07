---
title: towctrans
ms.date: 11/04/2016
api_name:
- towctrans
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
- api-ms-win-crt-string-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- towctrans
helpviewer_keywords:
- towctrans function
ms.assetid: 1ed1e70d-7b31-490f-a7d9-42564b5924ca
ms.openlocfilehash: d63fc343647cd0f949f282e2a64d4a0636e62bd7
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957424"
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

**Towctrans**在*类*中使用转换规则后的字符*c*。

## <a name="remarks"></a>备注

此*类别*的值必须已由之前对[wctrans](wctrans.md)的成功调用返回。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**towctrans**|\<wctype.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

有关使用**towctrans**的示例，请参阅**wctrans** 。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
