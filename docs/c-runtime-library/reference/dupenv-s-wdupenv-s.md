---
title: _dupenv_s、_wdupenv_s | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
dev_langs:
- C++
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0e2a89679c8ca564236e1c9d1eccfee274eb4116
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/20/2018
---
# <a name="dupenvs-wdupenvs"></a>_dupenv_s、_wdupenv_s

从当前环境中获取值。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
errno_t _dupenv_s(
   char **buffer,
   size_t *numberOfElements,
   const char *varname
);
errno_t _wdupenv_s(
   wchar_t **buffer,
   size_t *numberOfElements,
   const wchar_t *varname
);
```

### <a name="parameters"></a>参数

*buffer*<br/>
用于存储变量值的缓冲区。

*numberOfElements*<br/>
大小*缓冲区*。

*varname*<br/>
环境变量名称。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

这些函数验证其参数;如果*缓冲区*或*varname*是**NULL**中, 所述，将调用无效参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则函数将设置**errno**到**EINVAL**并返回**EINVAL**。

如果这些函数无法分配足够的内存，则它们设置*缓冲区*到**NULL**和*numberOfElements*为 0，然后返回**ENOMEM**。

## <a name="remarks"></a>备注

**_Dupenv_s**函数将搜索的环境变量列表*varname*。 如果找到该变量，则 **_dupenv_s**分配一个缓冲区，并将变量的值复制到缓冲区。 在中返回缓冲区的地址和长度*缓冲区*和*numberOfElements*。 通过分配的缓冲区本身， **_dupenv_s**提供一个更方便的替代方法[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)。

> [!NOTE]
> 调用程序负责通过调用 [free](free.md) 释放内存。

如果未找到该变量，*缓冲区*设置为**NULL**， *numberOfElements*设置为 0，并且返回值为 0，因为这种情况下不被视为错误条件。

如果你不感兴趣的缓冲区的大小可以传递**NULL**为*numberOfElements*。

**_dupenv_s**不区分大小写，在 Windows 操作系统中。 **_dupenv_s**使用由全局变量指向该环境的副本 **_environ**来访问该环境。 请参阅中的备注部分[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)有关的讨论 **_environ**。

中的值*缓冲区*副本的环境变量的值; 对其进行修改具有对该环境没有影响。 请使用 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md) 函数修改环境变量的值。

**_wdupenv_s**是宽字符版本的 **_dupenv_s**; 的自变量 **_wdupenv_s**是宽字符字符串。 **_Wenviron**全局变量是宽字符版本的 **_environ**。 请参阅中的备注部分[getenv_s、 _wgetenv_s](getenv-s-wgetenv-s.md)有关的详细信息 **_wenviron**。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_dupenv_s.c
#include  <stdlib.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s( &pValue, &len, "pathext" );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s( &pValue, &len, "nonexistentvariable" );
   if ( err ) return -1;
   printf( "nonexistentvariable = %s\n", pValue );
   free( pValue ); // It's OK to call free with NULL
}
```

```Output
pathext = .COM;.EXE;.BAT;.CMD;.VBS;.VBE;.JS;.JSE;.WSF;.WSH;.pl
nonexistentvariable = (null)
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[环境常量](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg、_wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)<br/>
