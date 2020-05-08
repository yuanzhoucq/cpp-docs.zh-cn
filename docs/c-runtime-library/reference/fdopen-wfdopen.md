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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 227f9e31c689b0259c429e2ffd9fce074903bd71
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2020
ms.locfileid: "82920181"
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

*fd*<br/>
打开文件的文件描述符。

*mode*<br/>
文件访问的类型。

## <a name="return-value"></a>返回值

这些函数均返回指向打开流的指针。 一个 null 指针值指示错误。 出现错误时，会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则将**errno**设置为**ebadf (**，这指示错误的文件描述符或**EINVAL**，这表示*模式*为空指针。

有关这些及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Fdopen**函数将 i/o 流与由*fd*标识的文件相关联，从而允许对为低级别 i/o 而打开的文件进行缓冲和格式化。 **_wfdopen**是 **_fdopen**的宽字符版本;**_wfdopen**的*mode*参数是宽字符字符串。 **_wfdopen**和 **_fdopen**的行为方式相同。

传递给 **_fdopen**的文件描述符由返回的**文件 &#42;** 流拥有。 如果 **_fdopen**成功，则不要在文件描述符上调用[ \_close](close.md) 。 对返回的 **&#42;文件**调用[fclose](fclose-fcloseall.md)也会关闭文件说明符。

默认情况下，此函数的全局状态的作用域限定为应用程序。 若要更改此项，请参阅[CRT 中的全局状态](../global-state.md)。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|\_未定义\_UNICODE 和 MBCS|\_定义 MBCS|\_已定义 UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tfdopen**|**_fdopen**|**_fdopen**|**_wfdopen**|

*模式*字符串指定为文件请求的文件访问类型：

| *mode* | 访问 |
|--------|--------|
| **迅驰** | 打开以便读取。 如果文件不存在或找不到，则**fopen**调用失败。 |
| **水平** | 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。 |
| **的** | 打开以在文件末尾进行写入（追加）。 创建文件（如果文件不存在）。 |
| **"r +"** | 打开以便读取和写入。 文件必须存在。 |
| **"w +"** | 打开用于读取和写入的空文件。 如果文件存在，则其内容会被销毁。 |
| **"a +"** | 打开以进行读取和追加。 创建文件（如果文件不存在）。 |

使用 **"a"** 或 **"a +"** 访问类型打开文件时，所有写入操作都将在文件末尾进行。 可以通过使用[fseek](fseek-fseeki64.md)或[倒带](rewind.md)重定位文件指针，但在执行任何写入操作之前，该指针始终会移回文件末尾。因此，无法覆盖现有数据。 指定 **"r +"**、 **"w +"** 或 **"a +"** 访问类型时，允许读取和写入（文件称为 "更新"）。 但是，在读取和写入之间切换时，必须有干预[fflush](fflush.md)、 [fsetpos](fsetpos.md)、 [fseek](fseek-fseeki64.md)或[倒带](rewind.md)操作。 如果需要，可以为[fsetpos](fsetpos.md)或[fseek](fseek-fseeki64.md)操作指定当前位置。

除了以上值之外，还可以在*模式*中包含以下字符以指定换行符的转换模式：

| *模式*修饰符 | 行为 |
|-----------------|----------|
| **关心** | 在文本（转换）模式下打开。 在这种模式下，输入时，回车换行 (CR-LF) 组合将转换为单一的换行 (LF)；输出时，LF 字符将转换为 CR-LF 组合。 CTRL+Z 也将在输入时解释为文件尾字符。 |
| **b** | 在二进制（未转换）模式下打开。 禁止任何来自**t**模式的翻译。 |
| **ansi-c** | 启用关联*文件名*的提交标志，以便在调用**fflush**或 **_flushall**时，将文件缓冲区的内容直接写入磁盘。 |
| **n** | 将关联的*文件名*的提交标志重置为 "无提交"。 这是默认设置。 如果将程序与 Commode.obj 链接，还会替代全局提交标志。全局提交标志默认为 "无提交"，除非你将程序显式链接到 Commode.obj。 |

**T**、 **c**和**n** *模式*选项是 Microsoft **fopen**和 **_fdopen**扩展。 如果要保留 ANSI 可移植性，请不要使用它们。

如果在*mode*中未给出**t**或**b** ，则默认转换模式由全局变量[ \_fmode](../../c-runtime-library/fmode.md)定义。 如果**t**或**b**作为参数的前缀，则函数将失败并返回 NULL。 有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。

**Fopen**和 **_fdopen**中使用的*模式*字符串的有效字符对应于在[ \_open](open-wopen.md)和[ \_sopen](sopen-wsopen.md)中使用的*oflag*参数，如下表所示：

|*模式*字符串中的字符|**_Open**和 **_sopen**的等效*oflag*值|
|---------------------------------|---------------------------------------------------|
|**的**|**\_O\_WRONLY &#124; \_o\_append** （通常** \_为\_o WRONLY \_&#124;\_o 将\_&#124;\_o append**）|
|**a +**|**\_O\_RDWR &#124; \_o\_append** （通常** \_为\_o RDWR \_&#124;\_o append \_&#124;\_o append** ）|
|**r**|**\_O\_RDONLY**|
|**r +**|**\_O\_RDWR**|
|**w**|**\_O\_WRONLY** （通常** \_为\_o WRONLY \_&#124;\_o 将\_&#124;\_TRUNC**|
|**w +**|**\_O\_RDWR** （通常** \_为\_o RDWR \_&#124;\_o 将\_&#124;\_TRUNC**|
|**b**|**\_O\_二进制**|
|**关心**|**\_O\_文本**|
|**ansi-c**|None|
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

### <a name="output"></a>Output

```Output
Lines in file: 2
```

## <a name="see-also"></a>请参阅

[流 I/O](../../c-runtime-library/stream-i-o.md)<br/>
[\_dup、 \_dup2](dup-dup2.md)<br/>
[fclose、 \_fcloseall](fclose-fcloseall.md)<br/>
[fopen、 \_wfopen](fopen-wfopen.md)<br/>
[freopen、 \_wfreopen](freopen-wfreopen.md)<br/>
[\_open、 \_wopen](open-wopen.md)<br/>
