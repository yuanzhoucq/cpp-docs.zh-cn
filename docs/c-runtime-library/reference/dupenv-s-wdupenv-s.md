---
title: _dupenv_s、_wdupenv_s
ms.date: 11/04/2016
api_name:
- _dupenv_s
- _wdupenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- tdupenv_s
- _dupenv_s
- wdupenv_s
- dupenv_s
- _tdupenv_s
- _wdupenv_s
helpviewer_keywords:
- _dupenv_s function
- _tdupenv_s function
- _wdupenv_s function
- environment variables
- wdupenv_s function
- dupenv_s function
- tdupenv_s function
ms.assetid: b729ecc2-a31d-4ccf-92a7-5accedb8f8c8
ms.openlocfilehash: f66828e0941c2324d75797cbb1fa77bdfa184205
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942025"
---
# <a name="_dupenv_s-_wdupenv_s"></a>_dupenv_s、_wdupenv_s

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
*缓冲区*的大小。

*varname*<br/>
环境变量名称。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

这些函数验证其参数;如果*buffer*或*varname*为**NULL**，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数会将**errno**设置为**EINVAL**并返回**EINVAL**。

如果这些函数无法分配足够的内存，它们会将*缓冲区*设置为**NULL** ，将*numberOfElements*设置为0，并返回**ENOMEM**。

## <a name="remarks"></a>备注

**_Dupenv_s**函数搜索*varname*的环境变量列表。 如果找到变量， **_dupenv_s**将分配一个缓冲区，并将该变量的值复制到缓冲区中。 缓冲区的地址和长度在*buffer*和*numberOfElements*中返回。 通过分配缓冲区本身， **_dupenv_s**为[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)提供了更方便的替代方法。

> [!NOTE]
> 调用程序负责通过调用 [free](free.md) 释放内存。

如果找不到该变量，则*buffer*设置为**NULL**， *numberOfElements*设置为0，并且返回值为0，因为这种情况不会被视为错误条件。

如果你对缓冲区大小不感兴趣，则可以为*numberOfElements*传递**NULL** 。

Windows 操作系统中的 **_dupenv_s**不区分大小写。 **_dupenv_s**使用全局变量 **_environ**指向的环境副本来访问该环境。 有关 **_environ**的讨论[，请参阅 getenv_s、_Wgetenv_s](getenv-s-wgetenv-s.md)中的备注。

*Buffer*中的值是环境变量值的副本;修改它不会影响环境。 请使用 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md) 函数修改环境变量的值。

**_wdupenv_s**是 **_dupenv_s**的宽字符版本; **_wdupenv_s**的参数是宽字符字符串。 **_Wenviron**全局变量是 **_environ**的宽字符版本。 有关 **_wenviron**的详细信息，请参阅[getenv_s，_Wgetenv_s](getenv-s-wgetenv-s.md)中的备注。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
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
