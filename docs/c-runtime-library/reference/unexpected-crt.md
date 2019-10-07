---
title: unexpected (CRT)
ms.date: 11/04/2016
api_name:
- unexpected
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
- unexpected
helpviewer_keywords:
- unexpected function
ms.assetid: 2f873763-15ad-4556-a924-dcf28f2b52b4
ms.openlocfilehash: 796f5ddbf8467656b5430de1d504f162d891864d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957823"
---
# <a name="unexpected-crt"></a>unexpected (CRT)

调用**terminate**或使用**set_unexpected**指定的函数。

## <a name="syntax"></a>语法

```C
void unexpected( void );
```

## <a name="remarks"></a>备注

异常处理的当前实现不使用**异常例程。** C++ 默认情况下，**意外**调用**终止**。 可以通过以下方式更改此默认行为：编写自定义终止函数并调用**set_unexpected**作为其参数的函数的名称。 **意外**调用作为**set_unexpected**的参数提供的最后一个函数。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**unexpected**|\<eh.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[异常处理例程](../../c-runtime-library/exception-handling-routines.md)<br/>
[abort](abort.md)<br/>
[_set_se_translator](set-se-translator.md)<br/>
[set_terminate](set-terminate-crt.md)<br/>
[set_unexpected](set-unexpected-crt.md)<br/>
[terminate](terminate-crt.md)<br/>
