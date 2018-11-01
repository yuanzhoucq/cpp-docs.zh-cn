---
title: wctype
ms.date: 11/04/2016
apiname:
- wctype
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
apitype: DLLExport
f1_keywords:
- wctype
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
ms.openlocfilehash: 81caf8e1ab04635d205d7b01af2d4c2896eec01c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456896"
---
# <a name="wctype"></a>wctype

确定宽字符代码的分类规则。

## <a name="syntax"></a>语法

```C
wctype_t wctype(
   const char * property
);
```

### <a name="parameters"></a>参数

*属性*<br/>
属性字符串。

## <a name="return-value"></a>返回值

如果**LC_CTYPE**的当前区域设置类别未定义其名称与属性的字符串匹配的分类规则*属性*，该函数将返回零。 否则，它将返回一个适合用作对 [towctrans](towctrans.md) 的后续调用的第二个参数的非零值。

## <a name="remarks"></a>备注

此函数将确定宽字符代码的分类规则。 以下调用对在所有区域设置中具有相同的行为（但实现可定义其他分类规则，甚至在“C”区域设置中）：

|函数|与以下项相同|
|--------------|-------------|
|iswalnum(c)|iswctype (c、 wctype ("alnum"))|
|iswalpha(c)|iswctype (c、 wctype ("alpha"))|
|iswcntrl(c)|iswctype (c、 wctype （"控件"）)|
|iswdigit(c)|iswctype (c、 wctype （"数字"）)|
|iswgraph(c)|iswctype (c、 wctype （"关系图"）)|
|iswlower(c)|iswctype (c、 wctype （"较低"）)|
|iswprint(c)|iswctype (c、 wctype ("print"))|
|iswpunct(c)|iswctype (c、 wctype ("punct"))|
|iswspace(c)|iswctype (c、 wctype （"空间"）)|
|iswupper(c)|iswctype (c、 wctype （"大写"）)|
|iswxdigit(c)|iswctype (c、 wctype ("xdigit"))|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
