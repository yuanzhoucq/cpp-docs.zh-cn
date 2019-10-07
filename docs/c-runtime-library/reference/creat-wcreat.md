---
title: _creat、_wcreat
ms.date: 11/04/2016
api_name:
- _creat
- _wcreat
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
ms.openlocfilehash: d278bffbfdf856956a20b01da4dad2ba00952359
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938893"
---
# <a name="_creat-_wcreat"></a>_creat、_wcreat

新建文件。 已不推荐使用 **_creat**和 **_wcreat** ;改用[_sopen_s、_wsopen_s](sopen-s-wsopen-s.md) 。

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

如果成功，则这些函数将文件描述符返回到已创建文件。 否则，函数将返回-1 并设置**errno** ，如下表所示。

|**errno**设置|描述|
|---------------------|-----------------|
|**EACCES**|*filename*指定现有的只读文件，或者指定目录而不是文件。|
|**EMFILE**|没有更多可用的文件描述符。|
|**ENOENT**|找不到指定的文件。|

如果*filename*为**NULL**，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续, 则这些函数会将**errno**设置为**EINVAL** , 并返回-1。

有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Creat**函数将创建一个新文件，或者打开并截断现有文件。 **_wcreat**是 **_creat**的宽字符版本; **_wcreat**的*filename*参数是宽字符字符串。 否则， **_wcreat**和 **_creat**的行为相同。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tcreat**|**_creat**|**_creat**|**_wcreat**|

如果*filename*指定的文件不存在，则将使用给定的权限设置创建一个新文件，并打开该文件以进行写入。 如果该文件已存在并且其权限设置允许写入，则 **_creat**会将该文件截断到 length 0，销毁以前的内容，然后将其打开以进行写入。 权限设置*pmode*仅适用于新创建的文件。 新文件第一次关闭后收到指定的权限设置。 整数表达式*pmode*包含一个或两个清单常量 **_S_IWRITE**和 **_S_IREAD**，在 sys\stat.h 中定义。 当同时提供两个常量时，它们将与按位 or 运算符 **&#124;** （）联接。 *Pmode*参数设置为以下值之一。

|值|定义|
|-----------|----------------|
|**_S_IWRITE**|允许写入。|
|**_S_IREAD**|允许读取。|
|**_S_IREAD** &#124; **_S_IWRITE**|允许读取和写入。|

如果未授予写入权限，则该文件为只读。 所有文件始终具有可读性；不能提供只写权限。 **_S_IWRITE**和 **_S_IREAD** |  **_S_IWRITE**模式是等效的。 使用 **_creat**打开的文件始终以兼容模式打开（请参阅[_Sopen](sopen-wsopen.md)）和 **_SH_DENYNO**。

在设置权限之前， **_creat**会将当前文件权限掩码应用到*pmode* （请参阅[_umask](umask.md)）。 提供 **_creat**主要是为了与以前的库兼容。 在*oflag*参数中对 **_open**使用 **_O_CREAT**和 **_O_TRUNC**的调用等效于 **_creat** ，并且更适用于新代码。

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|可选标头|
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
