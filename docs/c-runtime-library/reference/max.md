---
title: __max | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __max
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
- max
- __max
dev_langs:
- C++
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d223f4288ccf40646e8f560cec7243b7e8f9f649
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32398414"
---
# <a name="max"></a>__max

返回较大的两个值的预处理器宏。

## <a name="syntax"></a>语法

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>参数

， *b*<br/>
要比较的任何数字类型的值。

## <a name="return-value"></a>返回值

**__max**返回其自变量的较大。

## <a name="remarks"></a>备注

**__Max**宏比较两个值，并返回较大一的值。 参数可以是任何数字数据类型，有符号或无符号均可。 两个自变量以及返回值必须是同一数据类型。

返回自变量的计算两次由宏。 这可能导致意外结果，如果参数是一个表达式，它计算时，如更改其值`*p++`。

## <a name="requirements"></a>要求

|宏|必需的标头|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [__min](min.md) 中的示例。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>