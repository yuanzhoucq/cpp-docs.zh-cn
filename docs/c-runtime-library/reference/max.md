---
title: __max
ms.date: 04/05/2018
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
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 32e1207ea4bb030ac5303de32c0566f98e0596a3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156858"
---
# <a name="max"></a>__max

返回较大的两个值的预处理器宏。

## <a name="syntax"></a>语法

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>参数

*a*, *b*<br/>
要比较的任何数字类型的值。

## <a name="return-value"></a>返回值

**__max**返回其参数的较大。

## <a name="remarks"></a>备注

**__Max**宏将两个值进行比较并返回其中的较大的值。 参数可以是任何数字数据类型，有符号或无符号均可。 两个自变量以及返回值必须是同一数据类型。

返回参数的计算两次由宏。 这可能导致意外的结果，如果参数为一个表达式，它计算时，如来更改其值`*p++`。

## <a name="requirements"></a>要求

|宏|必需的标头|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>示例

有关详细信息，请参阅 [__min](min.md) 中的示例。

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>