---
title: _access、_waccess
ms.date: 11/04/2016
apiname:
- _access
- _waccess
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
- api-ms-win-crt-filesystem-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _waccess
- _access
- taccess
- waccess
- _taccess
helpviewer_keywords:
- access function
- _taccess function
- waccess function
- _access function
- _waccess function
- taccess function
ms.assetid: ba34f745-85c3-49e5-a7d4-3590bd249dd3
ms.openlocfilehash: 87ac912ab47483929b3afc2357331f8d97264b31
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50565472"
---
# <a name="access-waccess"></a>_access、_waccess

确定文件是否是只读的。 提供更多的安全版本；请参阅 [_access_s、_waccess_s](access-s-waccess-s.md)。

## <a name="syntax"></a>语法

```C
int _access(
   const char *path,
   int mode
);
int _waccess(
   const wchar_t *path,
   int mode
);
```

### <a name="parameters"></a>参数

*path*<br/>
文件或目录路径。

*模式*<br/>
读取/写入属性。

## <a name="return-value"></a>返回值

如果该文件具有给定的模式，则每个函数将返回 0。 如果命名的文件不存在或没有给定的模式，则函数将返回-1在这种情况下，`errno`下表中所示设置。

|||
|-|-|
`EACCES`|拒绝访问：文件的权限设置不允许指定的访问权限。
`ENOENT`|未找到文件名或路径。
`EINVAL`|参数无效。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

与文件一起使用时 **_access**函数将确定是否指定的文件或目录存在并且具有指定的值的属性*模式*。 与目录一起使用时 **_access**仅确定指定的目录是否存在; 在 Windows 2000 及更高版本操作系统中，所有目录具有读取和写入访问权限。

|*模式*值|文件检查内容|
|------------------|---------------------|
|00|仅检查是否存在|
|02|只写|
|04|只读|
|06|读取和写入|

此函数仅检查文件和目录是否为只读，不检查文件系统安全设置。 因此，你需要访问令牌。 有关文件系统安全性的详细信息，请参阅[访问令牌](/windows/desktop/SecAuthZ/access-tokens)。 存在 ATL 类以提供此功能；请参阅 [CAccessToken 类](../../atl/reference/caccesstoken-class.md)。

**_waccess**是宽字符版本 **_access**;*路径*参数 **_waccess**是宽字符字符串。 **_waccess**并 **_access**行为相同。

此函数验证其参数。 如果*路径*为 NULL 或*模式*未指定有效的模式下，将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许继续执行，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<wchar.h> 或 \<io.h>|\<errno.h>|

## <a name="example"></a>示例

下面的示例使用 **_access**来检查名为 crt_ACCESS 的文件。若要查看其是否存在以及是否允许写入 C。

```C
// crt_access.c
// compile with: /W1
// This example uses _access to check the file named
// crt_ACCESS.C to see if it exists and if writing is allowed.

#include  <io.h>
#include  <stdio.h>
#include  <stdlib.h>

int main( void )
{
    // Check for existence.
    if( (_access( "crt_ACCESS.C", 0 )) != -1 )
    {
        printf_s( "File crt_ACCESS.C exists.\n" );

        // Check for write permission.
        // Assume file is read-only.
        if( (_access( "crt_ACCESS.C", 2 )) == -1 )
            printf_s( "File crt_ACCESS.C does not have write permission.\n" );
    }
}
```

```Output
File crt_ACCESS.C exists.
File crt_ACCESS.C does not have write permission.
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 函数](stat-functions.md)