---
title: _fdopen、_wfdopen
ms.date: 4/2/2020
api_name:
- _fdopen
- _wfdopen
- _o__fdopen
- _o__wfdopen
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
- api-ms-win-crt-math-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tfdopen
- _fdopen
- _wfdopen
- wfdopen
- tfdopen
helpviewer_keywords:
- wfdopen function
- _fdopen function
- _wfdopen function
- tfdopen function
- fdopen function
- _tfdopen function
- streams, associating with files
ms.assetid: 262757ff-1e09-4472-a5b6-4325fc28f971
ms.openlocfilehash: 82a7e891e8bd6031ebbf761534b6df7cd8488d36
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347391"
---
# <a name="_fdopen-_wfdopen"></a>_fdopen、_wfdopen

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

*Fd*<br/>
打开文件的文件描述符。

*模式*<br/>
文件访问的类型。

## <a name="return-value"></a>返回值

这些函数均返回指向打开流的指针。 一个 null 指针值指示错误。 出现错误时，会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行 **，errno**将设置为**EBADF**，指示错误的文件描述符， 或**EINVAL**， 指示*模式*是空指针。

有关这些及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_fdopen**函数将 I/O 流与*fd*标识的文件关联，从而允许对为低级 I/O 打开的文件进行缓冲和格式化。 **_wfdopen**是 **_fdopen**的宽字符版本;_wfdopen*模式*参数是 **_wfdopen**宽字符字符串。 **_wfdopen**和 **_fdopen**否则行为相同。

传递到 **_fdopen**的文件描述符由返回的**FILE &#42;** 流所有。 如果 **_fdopen**成功，请不要在文件描述符上调用[\_关闭](close.md)。 在返回的 FILE**上**调用[fclose&#42;](fclose-fcloseall.md)也会关闭文件描述符。

默认情况下，此函数的全局状态范围为应用程序。 要更改此情况，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|\_未定义\_UNICODE 和 MBCS|\_MBCS 已定义|\_已定义 UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*模式*字符串指定为文件请求的文件访问类型：

| *模式* | 访问 |
|--------|--------|
| **"r"** | 打开以便读取。 如果文件不存在或找不到，**则 fopen**调用将失败。 |
| **"w"** | 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。 |
| **"a"** | 打开以在文件末尾写入（追加）。 创建文件（如果文件不存在）。 |
| **"r+"** | 打开以便读取和写入。 文件必须存在。 |
| **"w+"** | 打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。 |
| **"a+"** | 打开以进行读取和追加。 创建文件（如果文件不存在）。 |

当使用 **"a"或"a+"** 访问 **"a+"** 类型打开文件时，所有写入操作都发生在文件的末尾。 可以使用[fseek](fseek-fseeki64.md)或[后退](rewind.md)重新定位文件指针，但在执行任何写入操作之前，该文件指针始终被移回文件末尾。因此，无法覆盖现有数据。 指定 **"r+"、"w+"** 或 **"w+"****"a+"** 访问类型时，允许读取和写入（该文件表示为"更新"打开）。 但是，当您在阅读和写作之间切换时，必须有一个中间的 fflush、fsetpos、fseek 或[倒带](rewind.md)操作。 [fflush](fflush.md) [fsetpos](fsetpos.md) [fseek](fseek-fseeki64.md) 如果需要，可以指定[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作的当前位置。

除上述值外，还可以在*模式下*包含以下字符，以指定换行符的转换模式：

| *模式*修改器 | 行为 |
|-----------------|----------|
| **t** | 在文本（转换）模式下打开。 在这种模式下，输入时，回车换行 (CR-LF) 组合将转换为单一的换行 (LF)；输出时，LF 字符将转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。 |
| **B** | 在二进制（未转换）模式下打开。 禁止从**t**模式的任何转换。 |
| **C** | 启用关联*文件名*的提交标志，以便在调用**fflush**或 **_flushall**时，文件缓冲区的内容直接写入磁盘。 |
| **n** | 将关联*文件名*的提交标志重置为"不提交"。 这是默认值。 如果将程序与 Commode.obj 链接，它还会覆盖全局提交标志。全局提交标志默认值为"不提交"，除非您将程序与 Commode.obj 显式链接。 |

**t、c**和**n** *模式*选项是 Microsoft**用于 fopen**和 **_fdopen**的扩展。 **c** 如果要保留 ANSI 可移植性，请不要使用它们。

如果在*模式下*未给出**t**或**b，** 则默认转换模式由全局变量[\_fmode](../../c-runtime-library/fmode.md)定义。 如果**t**或**b**预固定到参数，则函数将失败并返回 NULL。 有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

**fopen**和 **_fdopen**中使用的*模式*字符串的有效字符对应于[\_open](open-wopen.md)和[\_sopen](sopen-wsopen.md)中使用的*滞后*参数，如下表所示：

|*模式*字符串中的字符|**_open**和 **_sopen**的*滞后*值等价值|
|---------------------------------|---------------------------------------------------|
|**a**|**\_O\_WRONLY \_\_&#124; O APPEND（** 通常**\_O\_WRONLY &#124; \_\_O CREAT &#124; \_O\_APPEND）**|
|**a+**|**\_O\_RDWR \_\_&#124; O APPEND（** 通常**\_O\_RDWR &#124; \_\_O APPEND &#124; \_O\_CREAT** ）|
|**R**|**\_O\_RDONLY**|
|**r+**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** （通常**\_\_O \_\_WRONLY \_&#124;\_O CREAT &#124; O TRUNC**）|
|**w***|**\_O\_RDWR** （通常**\_\_O \_\_RDWR \_&#124;\_O CREAT &#124; O TRUNC**）|
|**B**|**\_O\_BINARY**|
|**t**|**\_O\_文本**|
|**C**|None|
|**n**|None|

## <a name="requirements"></a>要求

|函数|必需的标头|
|--------------|---------------------|
|**_fdopen**|\<stdio.h>|
|**_wfdopen**|\<stdio.h> 或 \<wchar.h>|

有关兼容性的详细信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。

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

### <a name="input-crt_fdopentxt"></a>输入：crt_fdopen.txt

```Input
Line one
Line two
```

### <a name="output"></a>输出

```Output
Lines in file: 2
```

## <a name="see-also"></a>另请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[\_欺骗，\_欺骗2](dup-dup2.md)<br/>
[fclose， \_fcloseall](fclose-fcloseall.md)<br/>
[开，wfopen \_](fopen-wfopen.md)<br/>
[弗赖恩\_，wf重新](freopen-wfreopen.md)<br/>
[\_打开，\_打开](open-wopen.md)<br/>
