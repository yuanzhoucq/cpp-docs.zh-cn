---
title: _fpclass、_fpclassf
ms.date: 04/05/2018
api_name:
- _fpclass
- _fpclassf
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpclass
- _fpclass
- _fpclassf
- math/_fpclass
- float/_fpclass
- math/_fpclassf
helpviewer_keywords:
- fpclass function
- floating-point numbers, IEEE representation
- _fpclass function
- _fpclassf function
ms.assetid: 2774872d-3543-446f-bc72-db85f8b95a6b
ms.openlocfilehash: db95453a44f6a55d4bf98638351dcda4bd8377c9
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857835"
---
# <a name="_fpclass-_fpclassf"></a>_fpclass、_fpclassf

返回一个值，该值指示参数的浮点分类。

## <a name="syntax"></a>语法

```C
int _fpclass(
   double x
);

int _fpclassf(
   float x
); /* x64 only */
```

### <a name="parameters"></a>参数

*x*<br/>
要测试的浮点值。

## <a name="return-value"></a>返回值

**_Fpclass**和 **_fpclassf**函数返回一个整数值，该值指示参数*x*的浮点分类。 分类可能具有 \<float.h> 中定义的下列值之一。

|{2&gt;值&lt;2}|描述|
|-----------|-----------------|
|**_FPCLASS_SNAN**|信令 NaN|
|**_FPCLASS_QNAN**|静默 NaN|
|**_FPCLASS_NINF**|负无穷大（-INF）|
|**_FPCLASS_NN**|标准化的非零负值|
|**_FPCLASS_ND**|非标准化的负值|
|**_FPCLASS_NZ**|负零（-0）|
|**_FPCLASS_PZ**|正零 (+0)|
|**_FPCLASS_PD**|非标准化的正值|
|**_FPCLASS_PN**|标准化的非零正值|
|**_FPCLASS_PINF**|正无穷大 (+INF)|

## <a name="remarks"></a>备注

**_Fpclass**和 **_Fpclassf**函数是 Microsoft 特定的。 它们类似于 [fpclassify](fpclassify.md)，但返回有关参数的更多详情信息。 仅当为 x64 平台编译时， **_fpclassf**函数才可用。

## <a name="requirements"></a>需求

|函数|必需的标头|
|--------------|---------------------|
|**_fpclass**， **_fpclassf**|\<float.h>|

有关兼容性和符合性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[isnan、_isnan、_isnanf](isnan-isnan-isnanf.md)<br/>
[fpclassify](fpclassify.md)<br/>