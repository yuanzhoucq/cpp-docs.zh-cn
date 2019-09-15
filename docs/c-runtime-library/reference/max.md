---
title: __max
ms.date: 04/05/2018
api_name:
- __max
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: dac82ecd1c96d1edf9175a29797d93c65bc19c99
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70952754"
---
# <a name="__max"></a>__max

返回两个值中较大值的预处理器宏。

## <a name="syntax"></a>语法

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>参数

*a*、 *b*<br/>
要比较的任何数字类型的值。

## <a name="return-value"></a>返回值

**__max**返回其参数中的较大者。

## <a name="remarks"></a>备注

**__Max**宏比较两个值，并返回较大值的值。 参数可以是任何数字数据类型，有符号或无符号均可。 两个自变量以及返回值必须是同一数据类型。

返回的参数由宏计算两次。 如果参数是在计算时更改其值的表达式（如`*p++`），则这可能会导致意外的结果。

## <a name="requirements"></a>要求

|宏|必需的标头|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [__min](min.md) 中的示例。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>