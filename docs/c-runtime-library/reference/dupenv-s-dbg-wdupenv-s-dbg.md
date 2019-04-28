---
title: _dupenv_s_dbg、_wdupenv_s_dbg
ms.date: 11/04/2016
apiname:
- _dupenv_s_dbg
- _wdupenv_s_dbg
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
- _tdupenv_s_dbg
- _dupenv_s_dbg
- _wdupenv_s_dbg
helpviewer_keywords:
- _tdupenv_s_dbg function
- dupenv_s_dbg function
- _wdupenv_s_dbg function
- environment variables
- tdupenv_s_dbg function
- wdupenv_s_dbg function
- _dupenv_s_dbg function
ms.assetid: e3d81148-e24e-46d0-a21d-fd87b5e6256c
ms.openlocfilehash: 95d8c18a0ebc543304fdb6bf51c4adde589333aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62339216"
---
# <a name="dupenvsdbg-wdupenvsdbg"></a>_dupenv_s_dbg、_wdupenv_s_dbg

从当前环境中获取值。  [_dupenv_s、_wdupenv_s](dupenv-s-wdupenv-s.md) 的版本，使用 [_malloc_dbg](malloc-dbg.md) 来分配内存，以提供其他调试信息。

## <a name="syntax"></a>语法

```C
errno_t _dupenv_s_dbg(
   char **buffer,
   size_t *numberOfElements,
   const char *varname,
   int blockType,
   const char *filename,
   int linenumber
);
errno_t _wdupenv_s_dbg(
   wchar_t **buffer,
   size_t * numberOfElements,
   const wchar_t *varname,
   int blockType,
   const char *filename,
   int linenumber
);
```

### <a name="parameters"></a>参数

*buffer*<br/>
用于存储变量值的缓冲区。

*numberOfElements*<br/>
大小*缓冲区*。

*varname*<br/>
环境变量名称。

*blockType*<br/>
内存块的请求类型： **_CLIENT_BLOCK**或 **_NORMAL_BLOCK**。

*filename*<br/>
指向源文件的名称或**NULL**。

*linenumber*<br/>
源文件中的行数或**NULL**。

## <a name="return-value"></a>返回值

如果成功，则为零；如果失败，则为错误代码。

这些函数将验证其参数;如果*缓冲区*或*varname*是**NULL**，如中所述，将调用无效的参数处理程序[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则函数将设置**errno**到**EINVAL**并返回**EINVAL**。

如果这些函数无法分配足够的内存，则设置*缓冲区*到**NULL**并*numberOfElements*为 0，并返回**ENOMEM**。

## <a name="remarks"></a>备注

**_Dupenv_s_dbg**并 **_wdupenv_s_dbg**函数是相同 **_dupenv_s**并 **_wdupenv_s**只不过，当 **_DEBUG**是定义，这些函数将使用的调试版本[malloc](malloc.md)， [_malloc_dbg](malloc-dbg.md)来分配内存的环境变量的值。 有关调试功能的信息 **_malloc_dbg**，请参阅[_malloc_dbg](malloc-dbg.md)。

在大多数情况下，无需显式调用这些函数。 相反，可以定义标志 **_CRTDBG_MAP_ALLOC**。 当 **_CRTDBG_MAP_ALLOC**定义，则调用 **_dupenv_s**并 **_wdupenv_s**重新映射到 **_dupenv_s_dbg**和 **_wdupenv_s_dbg**分别具有*blockType*设置为 **_NORMAL_BLOCK**。 因此，不需要显式调用这些函数，除非你想要将标记作为堆块 **_CLIENT_BLOCK**。 有关块类型的详细信息，请参阅[调试堆中的块类型](/visualstudio/debugger/crt-debug-heap-details)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tdupenv_s_dbg**|**_dupenv_s_dbg**|**_dupenv_s_dbg**|**_wdupenv_s_dbg**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_dupenv_s_dbg**|\<crtdbg.h>|
|**_wdupenv_s_dbg**|\<crtdbg.h>|

有关其他兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_dupenv_s_dbg.c
#include  <stdlib.h>
#include <crtdbg.h>

int main( void )
{
   char *pValue;
   size_t len;
   errno_t err = _dupenv_s_dbg( &pValue, &len, "pathext",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
   if ( err ) return -1;
   printf( "pathext = %s\n", pValue );
   free( pValue );
   err = _dupenv_s_dbg( &pValue, &len, "nonexistentvariable",
      _NORMAL_BLOCK, __FILE__, __LINE__ );
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
[getenv_s、_wgetenv_s](getenv-s-wgetenv-s.md)<br/>
[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)<br/>
