---
title: _popen、_wpopen
ms.date: 11/04/2016
apiname:
- _popen
- _wpopen
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
- tpopen
- popen
- wpopen
- _popen
- _wpopen
- _tpopen
helpviewer_keywords:
- tpopen function
- pipes, creating
- _popen function
- _tpopen function
- popen function
- wpopen function
- _wpopen function
ms.assetid: eb718ff2-c87d-4bd4-bd2e-ba317c3d6973
ms.openlocfilehash: 5284685f56a73c4c7e48fce981745220651399a1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62156156"
---
# <a name="popen-wpopen"></a>_popen、_wpopen

创建一个管道并执行命令。

> [!IMPORTANT]
> 此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅[通用 Windows 平台应用中不支持的 CRT 函数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)。

## <a name="syntax"></a>语法

```C
FILE *_popen(
    const char *command,
    const char *mode
);
FILE *_wpopen(
    const wchar_t *command,
    const wchar_t *mode
);
```

### <a name="parameters"></a>参数

*command*<br/>
要执行的命令。

*模式*<br/>
返回流的模式。

## <a name="return-value"></a>返回值

返回一个与创建的管道一端相关联的流。 管道的另一端与生成的命令的标准输入或标准输出相关联。 函数针对错误返回 **NULL**。 如果错误是无效的参数，例如，如果*命令*或*模式*是 null 指针，或*模式*不是有效模式**errno**设置为**EINVAL**。 有关有效模式的信息，请参阅“备注”部分。

有关这些及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>备注

**_Popen**函数创建一个管道，并以异步方式执行使用指定的字符串的命令处理器的衍生的副本*命令*。 字符串 *mode* 指定请求的访问类型，如下所示。

|访问模式|描述|
|-|-|
|**“r”**|调用进程可使用返回的流读取生成的命令的标准输出。|
|**“w”**|调用进程可使用返回的流写入生成的命令的标准输入。|
|**“b”**|在二进制模式下打开。|
|**“t”**|在文本模式下打开。|

> [!NOTE]
> 如果在 Windows 程序中使用 **_popen**函数返回无效的文件指针，从而导致程序无限期停止响应。 **_popen**控制台应用程序中可正常工作。 若要创建 Windows 应用程序将重定向输入和输出，请参阅[重定向输入和输出创建的子进程](/windows/desktop/ProcThread/creating-a-child-process-with-redirected-input-and-output)Windows SDK 中。

**_wpopen**是宽字符版本 **_popen**;*路径*参数 **_wpopen**是宽字符字符串。 **_wpopen**并 **_popen**行为相同。

### <a name="generic-text-routine-mappings"></a>一般文本例程映射

|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tpopen**|**_popen**|**_popen**|**_wpopen**|

## <a name="requirements"></a>要求

|例程所返回的值|必需的标头|
|-------------|---------------------|
|**_popen**|\<stdio.h>|
|**_wpopen**|\<stdio.h> 或 \<wchar.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

[C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。

## <a name="example"></a>示例

```C
// crt_popen.c
/* This program uses _popen and _pclose to receive a
* stream of text from a system process.
*/

#include <stdio.h>
#include <stdlib.h>

int main( void )
{

   char   psBuffer[128];
   FILE   *pPipe;

        /* Run DIR so that it writes its output to a pipe. Open this
         * pipe with read text attribute so that we can read it
         * like a text file.
         */

   if( (pPipe = _popen( "dir *.c /on /p", "rt" )) == NULL )
      exit( 1 );

   /* Read pipe until end of file, or an error occurs. */

   while(fgets(psBuffer, 128, pPipe))
   {
      printf(psBuffer);
   }

   /* Close pipe and print return value of pPipe. */
   if (feof( pPipe))
   {
     printf( "\nProcess returned %d\n", _pclose( pPipe ) );
   }
   else
   {
     printf( "Error: Failed to read the pipe to the end.\n");
   }
}
```

### <a name="sample-output"></a>示例输出

此输出假定当前目录中只有一个文件扩展名为 .c 的文件。

```Output
Volume in drive C is CDRIVE
Volume Serial Number is 0E17-1702

Directory of D:\proj\console\test1

07/17/98  07:26p                   780 popen.c
               1 File(s)            780 bytes
                             86,597,632 bytes free

Process returned 0
```

## <a name="see-also"></a>请参阅

[进程和环境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pclose](pclose.md)<br/>
[_pipe](pipe.md)<br/>
