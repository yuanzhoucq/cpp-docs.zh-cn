---
title: __min | Microsoft 文档
ms.custom: ''
ms.date: 04/05/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- __min
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
- __min
- min
- _min
dev_langs:
- C++
helpviewer_keywords:
- __min macro
- min macro
- minimum macro
- _min macro
ms.assetid: 2037f26c-b48a-4a69-8870-22519f052a3c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0cc69cb018cda6fc093c570dab86a8df4cf396b7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="min"></a>__min

返回两个值的较小者预处理器宏。

## <a name="syntax"></a>语法

```C
#define __min(a,b) (((a) < (b)) ? (a) : (b))
```

### <a name="parameters"></a>参数

， *b*<br/>
值的任何类型**<** 运算符适用于。

## <a name="return-value"></a>返回值

两个参数中的较小者。

## <a name="remarks"></a>备注

**__Min**宏比较两个值，并返回较小的一个的值。 参数可以是任何数字数据类型，有符号或无符号均可。 两个自变量以及返回值必须是同一数据类型。

返回自变量的计算两次由宏。 这可能导致意外结果，如果参数是一个表达式，它计算时，如更改其值`*p++`。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**__min**|\<stdlib.h>|

## <a name="example"></a>示例

```C
// crt_minmax.c

#include <stdlib.h>
#include <stdio.h>

int main( void )
{
   int a = 10;
   int b = 21;

   printf( "The larger of %d and %d is %d\n",  a, b, __max( a, b ) );
   printf( "The smaller of %d and %d is %d\n", a, b, __min( a, b ) );
}
```

```Output
The larger of 10 and 21 is 21
The smaller of 10 and 21 is 10
```

## <a name="see-also"></a>请参阅

[浮点支持](../../c-runtime-library/floating-point-support.md)<br/>
[__max](max.md)<br/>
