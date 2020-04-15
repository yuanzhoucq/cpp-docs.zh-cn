---
title: _dupenv_s、_wdupenv_s
ms.date: 4/2/2020
api_name:
- _dupenv_s
- _wdupenv_s
- _o__dupenv_s
- _o__wdupenv_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: f65f1da3e8cef077df04d0bdb7eb2aaf75afd9fa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348061"
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

*缓冲区*<br/>
用于存储变量值的缓冲区。

*元素数*<br/>
*缓冲区*的大小 。

*瓦尔名称*<br/>
环境变量名称。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

这些函数验证其参数;如果*缓冲区*或*varname*为**NULL，** 则无效参数处理程序将调用参数[验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则函数将**errno**设置为**EINVAL**并返回**EINVAL**。

如果这些函数无法分配足够的内存，它们会将*缓冲区*设置为**NULL，** 将*元素数*设置为 0，并返回**ENOMEM**。

## <a name="remarks"></a>备注

**_dupenv_s**函数搜索*变量*的环境变量列表。 如果找到该变量 **，_dupenv_s**分配缓冲区并将变量的值复制到缓冲区中。 缓冲区的地址和长度以*缓冲区*和*元素数量*返回。 通过分配缓冲区本身 **，_dupenv_s**提供了一个更方便的getenv_s替代[，_wgetenv_s](getenv-s-wgetenv-s.md)。

> [!NOTE]
> 调用程序负责通过调用 [free](free.md) 释放内存。

如果未找到变量，则*缓冲区*设置为**NULL，***数字元素*设置为 0，返回值为 0，因为这种情况不被视为错误条件。

如果您对缓冲区的大小不感兴趣，则可以传递**NULL** *以表示元素数量*。

**_dupenv_s**在 Windows 操作系统中不区分大小写。 **_dupenv_s**使用全局变量 **_environ**指向的环境的副本来访问环境。 _wgetenv_sgetenv_s见备[getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md)言，讨论 **_environ。**

*缓冲区*中的值是环境变量值的副本;修改它对环境没有影响。 请使用 [_putenv_s、_wputenv_s](putenv-s-wputenv-s.md) 函数修改环境变量的值。

**_wdupenv_s**是 **_dupenv_s**的宽字符版本;**_wdupenv_s**的参数是宽字符字符串。 **_wenviron**全局变量是 **_environ**的宽字符版本。 请参阅[getenv_s，_wgetenv_s](getenv-s-wgetenv-s.md)有关 **_wenviron**的更多。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s**|**_dupenv_s**|**_dupenv_s**|**_wdupenv_s**|

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_dupenv_s**|\<stdlib.h>|
|**_wdupenv_s**|\<stdlib.h> 或 \<wchar.h>|

有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

## <a name="see-also"></a>另请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[环境常量](../../c-runtime-library/environmental-constants.md)<br/>
[_dupenv_s_dbg、_wdupenv_s_dbg](dupenv-s-dbg-wdupenv-s-dbg.md)<br/>
[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)<br/>
