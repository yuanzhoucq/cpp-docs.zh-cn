---
title: _get_wpgmptr
ms.date: 11/04/2016
apiname:
- _get_wpgmptr
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- get_wpgmptr
- _get_wpgmptr
helpviewer_keywords:
- _wpgmptr global variable
- get_wpgmptr function
- wpgmptr global variable
- _get_wpgmptr function
ms.assetid: a77cdd13-2303-4b7c-9a60-8debdbef2011
ms.openlocfilehash: 87738c8564b70df37a9f2fbdcc5e5ab80165af32
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/09/2018
ms.locfileid: "51329080"
---
# <a name="getwpgmptr"></a>_get_wpgmptr

获取当前值 **_wpgmptr**全局变量。

## <a name="syntax"></a>语法

```C
errno_t _get_wpgmptr(
   wchar_t **pValue
);
```

### <a name="parameters"></a>参数

*pValue*<br/>
若要使用的当前值填充的字符串指针 **_wpgmptr**变量。

## <a name="return-value"></a>返回值

如果成功，则返回零；如果失败，则返回错误代码。 如果*pValue*是**NULL**，如中所述，将调用无效的参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数可设置**errno**到**EINVAL** ，并返回**EINVAL**。

## <a name="remarks"></a>备注

只能调用 **_get_wpgmptr**如果你的程序具有宽的入口点，例如**wmain()** 或**wWinMain()**。 **_Wpgmptr**全局变量包含与宽字符字符串与进程相关联的可执行文件的完整路径。 有关详细信息，请参阅 [_pgmptr、_wpgmptr](../../c-runtime-library/pgmptr-wpgmptr.md)。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_get_wpgmptr**|\<stdlib.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>请参阅

[_get_pgmptr](get-pgmptr.md)<br/>
