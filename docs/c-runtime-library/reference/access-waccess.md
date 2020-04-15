---
title: _access、_waccess
ms.date: 4/2/2020
api_name:
- _access
- _waccess
- _o__access
- _o__waccess
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
- api-ms-win-crt-filesystem-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 98726726e14aacec75ed99adfa33016b40affd17
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81350876"
---
# <a name="_access-_waccess"></a>_access、_waccess

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

*路径*<br/>
文件或目录路径。

*模式*<br/>
读取/写入属性。

## <a name="return-value"></a>返回值

如果该文件具有给定的模式，则每个函数将返回 0。 如果命名文件不存在或没有给定模式，则函数返回 -1;在这种情况下，`errno`如下表所示。

|||
|-|-|
`EACCES`|拒绝访问：文件的权限设置不允许指定的访问权限。
`ENOENT`|未找到文件名或路径。
`EINVAL`|参数无效。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

当与文件一起使用时 **，_access**函数确定指定的文件或目录是否存在，并且具有*模式*的值指定的属性。 当与目录一起使用时 **，_access**仅确定指定的目录是否存在;_access在 Windows 2000 和更高版本的操作系统中，所有目录都具有读取和写入访问权限。

|*模式*值|文件检查内容|
|------------------|---------------------|
|00|仅检查是否存在|
|02|只写|
|04|只读|
|06|读取和写入|

此函数仅检查文件和目录是否为只读，不检查文件系统安全设置。 因此，你需要访问令牌。 有关文件系统安全性的详细信息，请参阅[访问令牌](/windows/win32/SecAuthZ/access-tokens)。 存在 ATL 类以提供此功能；请参阅 [CAccessToken 类](../../atl/reference/caccesstoken-class.md)。

**_waccess**是 **_access**的宽字符版本;**_waccess的***路径*参数是宽字符字符串。 **_waccess**和 **_access**行为相同。

此函数验证其参数。 如果*路径*为 NULL 或*模式*未指定有效模式，则调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则该函数将 `errno` 设置为 `EINVAL` 并返回 -1。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_taccess`|**_access**|**_access**|**_waccess**|

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|----------------------|
|**_access**|\<io.h>|\<errno.h>|
|**_waccess**|\<wchar.h> 或 \<io.h>|\<errno.h>|

## <a name="example"></a>示例

下面的示例使用 **_access**检查名为crt_ACCESS的文件。C 以查看它是否存在以及是否允许写入。

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

## <a name="see-also"></a>另请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 函数](stat-functions.md)
