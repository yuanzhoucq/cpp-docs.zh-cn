---
title: wctype | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bb5003db02ed27c2906ebc3619313489e40e5fb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411895"
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

如果**LC_CTYPE**当前区域设置类别的未定义其名称与属性的字符串匹配的分类规则*属性*，函数将返回零。 否则，它将返回一个适合用作对 [towctrans](towctrans.md) 的后续调用的第二个参数的非零值。

## <a name="remarks"></a>备注

此函数将确定宽字符代码的分类规则。 以下调用对在所有区域设置中具有相同的行为（但实现可定义其他分类规则，甚至在“C”区域设置中）：

|函数|与以下项相同|
|--------------|-------------|
|iswalnum(c)|iswctype (c、 wctype ("alnum"))|
|iswalpha(c)|iswctype (c、 wctype ("alpha"))|
|iswcntrl(c)|iswctype (c、 wctype （"控件"）)|
|iswdigit(c)|iswctype (c、 wctype （"数字"）)|
|iswgraph(c)|iswctype (c、 wctype （"图形"）)|
|iswlower(c)|iswctype (c、 wctype （"低"）)|
|iswprint(c)|iswctype (c、 wctype （"打印"）)|
|iswpunct(c)|iswctype (c、 wctype （"标点符号"）)|
|iswspace(c)|iswctype (c、 wctype （"空间"）)|
|iswupper(c)|iswctype (c、 wctype （"上限"）)|
|iswxdigit(c)|iswctype (c、 wctype ("xdigit"))|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**wctype**|\<wctype.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[数据转换](../../c-runtime-library/data-conversion.md)<br/>
[setlocale、_wsetlocale](setlocale-wsetlocale.md)<br/>
