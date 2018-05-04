---
title: _fdopen、_wfdopen | Microsoft 文档
ms.custom: ''
ms.date: 12/12/2017
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _fdopen
- _wfdopen
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
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
dev_langs:
- C++
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 21bd849d5ce9560fae356869291d6764d613f0a7
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="fdopen-wfdopen"></a>_fdopen、_wfdopen

将流与以前为低级别 I/O 而打开的文件相关联。

## <a name="syntax"></a>语法

```C
FILE *_fdopen(
   int fd,
   const char *mode
);
FILE *_wfdopen(
   int fd,
   const wchar_t *mode
);
```

### <a name="parameters"></a>参数

*fd*打开的文件的文件描述符。

*模式*文件访问的类型。

## <a name="return-value"></a>返回值

这些函数均返回指向打开流的指针。 一个 null 指针值指示错误。 出现错误时，会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则**errno**设置为**EBADF**，指示错误的文件描述符或**EINVAL**，这指示*模式*是空指针。

有关这些及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Fdopen**函数将 I/O 流与由标识的文件相关联*fd*，从而允许对为低级别 I/O 进行缓冲和格式化打开的文件。 **_wfdopen**是宽字符版本的 **_fdopen**;*模式*参数 **_wfdopen**是宽字符字符串。 **_wfdopen**和 **_fdopen**否则具有相同行为。

文件描述符传递给 **_fdopen**拥有返回**文件&#42;** 流。 如果 **_fdopen**成功，请不要调用[\_关闭](close.md)上的文件描述符。 调用[fclose](fclose-fcloseall.md)对返回**文件&#42;** 也会关闭的文件描述符。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|\_UNICODE 和\_MBCS 未定义|\_MBCS 定义|\_UNICODE 定义|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*模式*字符串指定为文件请求的文件访问的类型：

|*模式*|Access|
|-|-|
**“r”**|打开以便读取。 如果文件不存在或找不到**fopen**调用将失败。
**“w”**|打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。
**“a”**|打开以进行写入 （追加），该文件末尾。 创建文件（如果文件不存在）。
**“r+”**|打开以便读取和写入。 文件必须存在。
**“w+”**|打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。
**“a+”**|打开以进行读取和追加。 创建文件（如果文件不存在）。

当用打开文件时 **"a"** 或 **"a +"** 访问类型，所有写入操作发生在文件末尾。 通过使用可重新定位文件指针[fseek](fseek-fseeki64.md)或[rewind](rewind.md)，但它将始终被移回文件末尾到任何写入操作执行前。因此，无法覆盖现有数据。 当 **"r +"**， **"w +"**，或 **"a +"** 指定访问类型，允许读取和写入 （文件将状态才能打开进行"更新"）。 但是，在读取与写入之间切换时，必须有中间[fflush](fflush.md)， [fsetpos](fsetpos.md)， [fseek](fseek-fseeki64.md)，或[rewind](rewind.md)操作。 你可以指定的当前位置[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作，但如果你愿意。

除了以上值，以下字符也可以包含在*模式*以指定换行符的转换模式：

|*模式*修饰符|行为|
|-|-|
**t**|在文本（转换）模式下打开。 在这种模式下，输入时，回车换行 (CR-LF) 组合将转换为单一的换行 (LF)；输出时，LF 字符将转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。
**b**|在二进制（未转换）模式下打开。 从任何翻译**t**模式将被抑制。
**c**|启用关联的提交标志*filename* ，以便将文件缓冲区的内容直接写入磁盘如果**fflush**或 **_flushall**调用。
**n**|关联的提交标志重置*filename*为"no-commit。" 这是默认设置。 如果将程序显式链接到 Commode.obj，它还将重写全局提交标志。除非将程序显式链接到 Commode.obj，全局提交标志默认为“no-commit”。

**T**， **c**，和**n** *模式*选项是 Microsoft 扩展**fopen**和 **_fdopen**。 如果要保留 ANSI 可移植性，请不要使用它们。

如果**t**或**b**中未给定*模式*，则默认转换模式由全局变量[ \_fmode](../../c-runtime-library/fmode.md)。 如果**t**或**b**前缀的自变量，函数将失败并返回 NULL。 有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

有效字符*模式*中使用字符串**fopen**和 **_fdopen**对应于*oflag*中使用自变量[\_打开](open-wopen.md)和[ \_sopen](sopen-wsopen.md)，此表中所示：

|中的字符*模式*字符串|等效*oflag*值 **_open**和 **_sopen**|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY &#124; \_O\_追加**(通常 **\_O\_WRONLY &#124; \_O\_CREAT &#124; \_O\_追加**)|
|**+**|**\_O\_RDWR &#124; \_O\_追加**(通常 **\_O\_RDWR &#124; \_O\_追加&#124; \_O\_CREAT** )|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** (通常 **\_O\_WRONLY &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**w +**|**\_O\_RDWR** (通常 **\_O\_RDWR &#124; \_O\_CREAT &#124; \_O\_TRUNC**)|
|**b**|**\_O\_BINARY**|
|**t**|**\_O\_TEXT**|
|**c**|无|
|**n**|无|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>示例

```c
// crt_fdopen.c
// This program opens a file by using low-level
// I/O, then uses _fdopen to switch to stream
// access. It counts the lines in the file.

#include <stdlib.h>
#include <stdio.h>
#include <fcntl.h>
#include <io.h>
#include <share.h>

int main( void )
{
   FILE *stream;
   int  fd, count = 0;
   char inbuf[128];

   // Open a file.
   if( _sopen_s( &fd, "crt_fdopen.txt", _O_RDONLY, _SH_DENYNO, 0 ) )
      exit( 1 );

   // Get stream from file descriptor.
   if( (stream = _fdopen( fd, "r" )) == NULL )
      exit( 1 );

   while( fgets( inbuf, 128, stream ) != NULL )
      count++;

   // After _fdopen, close by using fclose, not _close.
   fclose( stream );
   printf( "Lines in file: %d\n", count );
}
```

### <a name="input-crtfdopentxt"></a>输入：crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>输出

```Output
Lines in file: 2
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup、 \_dup2](dup-dup2.md)<br/>
[fclose、 \_fcloseall](fclose-fcloseall.md)<br/>
[fopen、 \_wfopen](fopen-wfopen.md)<br/>
[freopen、 \_wfreopen](freopen-wfreopen.md)<br/>
[\_打开， \_wopen](open-wopen.md)<br/>
