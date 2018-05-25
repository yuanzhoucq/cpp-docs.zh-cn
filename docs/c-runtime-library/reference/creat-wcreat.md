---
title: _creat、_wcreat | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1a6b987faa30439f0f374838fe7fcd4d942b8cc7
ms.sourcegitcommit: 6e3cf8df676d59119ce88bf5321d063cf479108c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/22/2018
---
# <a name="creat-wcreat"></a>_creat、_wcreat

新建文件。 **_creat**和 **_wcreat**已弃用; 使用[_sopen_s、 _wsopen_s](sopen-s-wsopen-s.md)相反。

## <a name="syntax"></a>语法

```C
int _creat(
   const char *filename,
   int pmode
);
int _wcreat(
   const wchar_t *filename,
   int pmode
);
```

### <a name="parameters"></a>参数

*filename*<br/>
新文件的名称。

*pmode*<br/>
权限设置。

## <a name="return-value"></a>返回值

如果成功，则这些函数将文件描述符返回到已创建文件。 否则，函数返回-1 并设置**errno**下表中所示。

|**errno**设置|描述|
|---------------------|-----------------|
|**EACCES**|*filename*指定现有只读文件或指定一个目录而不是文件。|
|**EMFILE**|没有更多可用的文件描述符。|
|**ENOENT**|找不到指定的文件。|

如果*filename*是**NULL**中, 所述，这些函数将调用无效参数处理程序，[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，则这些函数将设置**errno**到**EINVAL**并返回-1。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Creat**函数创建一个新文件或打开并将一个现有的截断。 **_wcreat**是宽字符版本的 **_creat**; *filename*参数 **_wcreat**是宽字符字符串。 **_wcreat**和 **_creat**否则具有相同行为。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

如果指定的文件*filename*不存在，新的文件使用给定的权限设置创建并打开以进行写入。 如果文件已存在，而且其权限设置允许写入， **_creat**截断为长度为 0，销毁以前的内容文件并将其打开以进行写入。 权限设置， *pmode*，适用于新创建的文件。 新文件第一次关闭后收到指定的权限设置。 整数表达式*pmode*包含一个或两个清单常量 **_S_IWRITE**和 **_S_IREAD**、 SYS\Stat.h 中定义。 当给定这两个常量时，它们是否联接的按位与或运算符 ( **&#124;** )。 *Pmode*参数设置为下列值之一。

|值|定义|
|-----------|----------------|
|**_S_IWRITE**|允许写入。|
|**_S_IREAD**|允许读取。|
|**_S_IREAD** &AMP;#124; **_S_IWRITE**|允许读取和写入。|

如果未授予写入权限，则该文件为只读。 所有文件始终具有可读性；不能提供只写权限。 模式 **_S_IWRITE**和 **_S_IREAD** | **_S_IWRITE**然后相等。 使用打开的文件 **_creat**始终在兼容性模式下打开 (请参阅[_sopen](sopen-wsopen.md)) 与 **_SH_DENYNO**。

**_creat**将当前文件权限掩码应用到*pmode*之前设置的权限 (请参阅[_umask](umask.md))。 **_creat**提供主要用于与以前的库的兼容性。 调用 **_open**与 **_O_CREAT**和 **_O_TRUNC**中*oflag*参数等效于 **_creat**也是新的代码更可取。

## <a name="requirements"></a>要求

|例程|必需的标头|可选标头|
|-------------|---------------------|---------------------|
|**_creat**|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|
|**_wcreat**|\<io.h> 或 \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```C
// crt_creat.c
// compile with: /W3
// This program uses _creat to create
// the file (or truncate the existing file)
// named data and open it for writing.

#include <sys/types.h>
#include <sys/stat.h>
#include <io.h>
#include <stdio.h>
#include <stdlib.h>

int main( void )
{
   int fh;

   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996
   // Note: _creat is deprecated; use _sopen_s instead
   if( fh == -1 )
      perror( "Couldn't create data file" );
   else
   {
      printf( "Created data file.\n" );
      _close( fh );
   }
}
```

```Output
Created data file.
```

## <a name="see-also"></a>请参阅

[低级别 I/O](../../c-runtime-library/low-level-i-o.md)<br/>
[_chmod、_wchmod](chmod-wchmod.md)<br/>
[_chsize](chsize.md)<br/>
[_close](close.md)<br/>
[_dup、_dup2](dup-dup2.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
[_sopen、_wsopen](sopen-wsopen.md)<br/>
[_umask](umask.md)<br/>
