---
title: "freopen、_wfreopen | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- freopen
- _wfreopen
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
- _wfreopen
- _tfreopen
- freopen
dev_langs: C++
helpviewer_keywords:
- _wfreopen function
- file pointers [C++], reassigning
- _tfreopen function
- freopen function
- tfreopen function
- wfreopen function
ms.assetid: de4b73f8-1043-4d62-98ee-30d2022da885
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: f25c4966b567d165be8f33a0c04f58ba0ac611b9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="freopen-wfreopen"></a>freopen、_wfreopen
重新分配文件指针。 提供这些函数的更安全版本；请参阅 [freopen_s、_wfreopen_s](../../c-runtime-library/reference/freopen-s-wfreopen-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
FILE *freopen(   
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
FILE *_wfreopen(   
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `path`  
 新文件的路径。  
  
 `mode`  
 允许的访问类型。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 这些函数均返回指向新打开的文件的指针。 如果发生错误，则关闭原始文件，且该函数返回 `NULL` 指针值。 如果 `path`、`mode` 或 `stream` 是 null 指针，或 `filename` 是空字符串，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `NULL`。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 提供这些函数的更安全版本；请参阅 [freopen_s、_wfreopen_s](../../c-runtime-library/reference/freopen-s-wfreopen-s.md)。  
  
 `freopen`函数关闭当前与关联的文件`stream`，并重新指定`stream`到指定的文件`path`。 `_wfreopen` 是 `_freopen` 的宽字符版本；`_wfreopen` 的 `path` 和 `mode` 参数是宽字符串。 除此以外，`_wfreopen` 和 `_freopen` 的行为完全相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tfreopen`|`freopen`|`freopen`|`_wfreopen`|  
  
 `freopen` 通常用于将预先打开的文件 `stdin`、`stdout` 和 `stderr` 重定向到用户指定的文件。 与关联的新文件`stream`使用打开`mode`，后者是一个字符串，指定，如下所示为该文件，请求的访问类型：  
  
 `"r"`  
 打开以便读取。 如果文件不存在或找不到，`freopen` 调用将失败。  
  
 `"w"`  
 打开用于写入的空文件。 如果给定文件存在，则其内容会被销毁。  
  
 `"a"`  
 打开以在文件末尾写入（追加），从而无需在将新数据写入文件之前移除 EOF 标记；如果文件不存在，则先创建文件。  
  
 `"r+"`  
 打开以便读取和写入。 （该文件必须存在。）  
  
 `"w+"`  
 打开用于读取和写入的空文件。 如果给定文件存在，则其内容会被销毁。  
  
 `"a+"`  
 打开以进行读取和追加；追加操作包括在新数据写入到文件之前移除 EOF 标记并在写入完成后还原 EOF 标记；如果文件不存在，则先创建文件。  
  
 使用 `"w"` 和 `"w+"` 类型时要小心，因为它们可能会破坏现有文件。  
  
 使用 `"a"` 或 `"a+"` 访问类型打开文件时，所有写入操作均将在文件末尾进行。 虽然使用 `fseek` 或 `rewind` 可重新定位文件指针，但在执行任何写入操作前，文件指针将始终被移回文件末尾。因此，无法覆盖现有数据。  
  
 在 EOF 标记追加到文件之前，`"a"` 模式不会将其删除。 在追加后，MS-DOS TYPE 命令只显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。 在 EOF 标记追加到文件之前，`"a+"` 模式会将其删除。 在追加后，MS-DOS TYPE 命令显示文件中的所有数据。 需使用 `"a+"` 模式才能附加到通过 CTRL+Z EOF 标记终止的流文件。  
  
 指定 `"r+"`、`"w+"` 或 `"a+"` 访问类型时，允许读取和写入（文件将处于打开状态以进行“更新”）。 但是，在读取与写入之间切换时，必须有干预性的 [fsetpos](../../c-runtime-library/reference/fsetpos.md)、[fseek](../../c-runtime-library/reference/fseek-fseeki64.md) 或 [rewind](../../c-runtime-library/reference/rewind.md) 操作。 如果需要的话，可以为 `fsetpos` 或 `fseek` 操作指定当前位置。 除上述值之外，还可以在 `mode` 字符串中包含以下字符之一以指定新行的转换模式。  
  
 `t`  
 在文本 （转换） 模式下打开;回车换行符 (CR-LF) 组合将转换为单一的换行 (LF) 字符输入;LF 字符将转换为 CR-LF 组合输出。 CTRL+Z 也将在输入时解释为文件尾字符。 在打开以便利用 `"a+"` 进行读取或读写的文件中，运行时库将检查文件末尾的 CTRL+Z，并在可能的情况下将其删除。 这是因为使用 `fseek` 和 `ftell` 在文件中移动时，可能导致 `fseek` 在文件末尾附近错误运行。 `t` 选项是一个 Microsoft 扩展，不应在需要 ANSI 可移植性的地方使用。  
  
 `b`  
 在二进制（未转换）模式下打开；禁止上述转换。  
  
 如果 `t` 或 `b` 在 `mode` 中未给出，则默认转换模式由全局变量 [_fmode](../../c-runtime-library/fmode.md) 定义。 如果 `t` 或 `b` 是该参数的前缀，则函数将失败并返回 `NULL`。  
  
 有关文本模式和二进制模式的讨论，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`freopen`|\<stdio.h>|  
|`_wfreopen`|\<stdio.h> 或 \<wchar.h>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_freopen.c  
// compile with: /W3  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   // Reassign "stderr" to "freopen.out":   
   stream = freopen( "freopen.out", "w", stderr ); // C4996  
   // Note: freopen is deprecated; consider using freopen_s instead  
  
   if( stream == NULL )  
      fprintf( stdout, "error on freopen\n" );  
   else  
   {  
      fprintf( stdout, "successfully reassigned\n" ); fflush( stdout );  
      fprintf( stream, "This will go to the file 'freopen.out'\n" );  
      fclose( stream );  
   }  
   system( "type freopen.out" );  
}  
```  
  
```Output  
successfully reassigned  
This will go to the file 'freopen.out'  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fclose、_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [_fdopen、_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_setmode](../../c-runtime-library/reference/setmode.md)