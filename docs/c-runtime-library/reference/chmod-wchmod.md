---
title: _chmod、_wchmod | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _chmod
- _wchmod
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
- _chmod
- _wchmod
- wchmod
dev_langs:
- C++
helpviewer_keywords:
- _chmod function
- wchmod function
- file permissions [C++]
- chmod function
- files [C++], changing permissions
- _wchmod function
ms.assetid: 92f7cb86-b3b0-4232-a599-b8c04a2f2c19
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0e4944f871195b276189014ed9d5d294b9b445fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="chmod-wchmod"></a>_chmod、_wchmod

更改文件权限设置。

## <a name="syntax"></a>语法

```C
int _chmod( const char *filename, int pmode );
int _wchmod( const wchar_t *filename, int pmode );
```

### <a name="parameters"></a>参数

*filename*<br/>
现有文件的名称。

*pmode*<br/>
该文件的权限设置。

## <a name="return-value"></a>返回值

如果成功更改权限设置，这些函数将返回 0。 返回值-1 表示失败。 如果找不到指定的文件， **errno**设置为**ENOENT**; 如果参数是无效的**errno**设置为**EINVAL**。

## <a name="remarks"></a>备注

**_Chmod**函数更改指定的文件的权限设置*filename*。 权限设置控制对文件的读取和写入访问权限。 整数表达式*pmode*包含一个或两个 SYS\Stat.h 中定义的以下清单常量。

|*pmode*|含义|
|-|-|
**_S_IREAD**|只允许读取。
**_S_IWRITE**|允许写入。 （实际上，允许读取和写入。）
**_S_IREAD** &AMP;#124; **_S_IWRITE**|允许读取和写入。

当给定这两个常量时，它们是否联接的按位与或运算符 (**|**)。 如果未授予写入权限，则该文件为只读。 注意，所有文件始终具有可读性；不能提供只写权限。 因此，模式 **_S_IWRITE**和 **_S_IREAD** | **_S_IWRITE**是等效的。

**_wchmod**是宽字符版本的 **_chmod**; *filename*参数 **_wchmod**是宽字符字符串。 **_wchmod**和 **_chmod**否则具有相同行为。

此函数验证其参数。 如果*pmode*不是清单常量之一的组合或合并了一组备用的常量，此函数只需将忽略那些。 如果*filename*是**NULL**，则调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则**errno**设置为**EINVAL**和该函数将返回-1。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tchmod**|**_chmod**|**_chmod**|**_wchmod**|

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_chmod**|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|
|**_wchmod**|\<io.h> 或 \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_chmod.c
// This program uses _chmod to
// change the mode of a file to read-only.
// It then attempts to modify the file.
//

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>
#include <errno.h>

// Change the mode and report error or success
void set_mode_and_report(char * filename, int mask)
{
   // Check for failure
   if( _chmod( filename, mask ) == -1 )
   {
      // Determine cause of failure and report.
      switch (errno)
      {
         case EINVAL:
            fprintf( stderr, "Invalid parameter to chmod.\n");
            break;
         case ENOENT:
            fprintf( stderr, "File %s not found\n", filename );
            break;
         default:
            // Should never be reached
            fprintf( stderr, "Unexpected error in chmod.\n" );
       }
   }
   else
   {
      if (mask == _S_IREAD)
        printf( "Mode set to read-only\n" );
      else if (mask & _S_IWRITE)
        printf( "Mode set to read/write\n" );
   }
   fflush(stderr);
}

int main( void )
{

   // Create or append to a file.
   system( "echo /* End of file */ >> crt_chmod.c_input" );

   // Set file mode to read-only:
   set_mode_and_report("crt_chmod.c_input ", _S_IREAD );

   system( "echo /* End of file */ >> crt_chmod.c_input " );

   // Change back to read/write:
   set_mode_and_report("crt_chmod.c_input ", _S_IWRITE );

   system( "echo /* End of file */ >> crt_chmod.c_input " );
}
```

```Output

A line of text.

```

```Output

      A line of text.Mode set to read-only
Access is denied.
Mode set to read/write
```

## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)<br/>
[_access、_waccess](access-waccess.md)<br/>
[_creat、_wcreat](creat-wcreat.md)<br/>
[_fstat、_fstat32、_fstat64、_fstati64、_fstat32i64、_fstat64i32](fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_stat、_wstat 函数](stat-functions.md)<br/>
