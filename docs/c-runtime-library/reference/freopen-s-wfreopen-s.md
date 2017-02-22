---
title: "freopen_s、_wfreopen_s | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_wfreopen_s"
  - "freopen_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "freopen_s"
  - "_tfreopen_s"
  - "_wfreopen_s"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tfreopen_s 函数"
  - "_wfreopen_s 函数"
  - "文件指针 [C++], 重新分配"
  - "freopen_s 函数"
  - "tfreopen_s 函数"
  - "wfreopen_s 函数"
ms.assetid: ad25a4da-6ad4-476b-a86d-660b221ca84d
caps.latest.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 27
---
# freopen_s、_wfreopen_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

重新分配文件指针。  如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述，这些 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md) 版本具有安全性增强功能。  
  
## 语法  
  
```  
errno_t freopen(   
   FILE** pFile,  
   const char *path,  
   const char *mode,  
   FILE *stream   
);  
errno_t _wfreopen(   
   FILE** pFile,  
   const wchar_t *path,  
   const wchar_t *mode,  
   FILE *stream   
);  
```  
  
#### 参数  
 \[out\] `pFile`  
 一个指针，指向由调用提供的文件指针。  
  
 \[in\] `path`  
 新文件的路径。  
  
 \[in\] `mode`  
 允许的访问类型。  
  
 \[in\] `stream`  
 指向 `FILE` 结构的指针。  
  
## 返回值  
 其中每个函数会返回一个错误代码。  如果发生错误，则关闭原始文件。  
  
## 备注  
 `freopen_s` 函数关闭当前与 `stream` 关联的文件，并重新指派 `stream` 到由 `path.` 指定的文件 `_wfreopen_s` 是宽字符版本的 `_freopen_s`；`_wfreopen_s` 的 `path` 和 `mode` 参数是宽字符字符串。  除此以外，`_wfreopen_s` 和 `_freopen_s` 的行为完全相同。  
  
 如果 `pFile`、`path`、`mode` 或 `stream` 中的任一个是 `NULL`，或如果 `path` 是一个空字符串，这些函数将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 `EINVAL`。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tfreopen_s`|`freopen_s`|`freopen_s`|`_wfreopen_s`|  
  
 `freopen_s` 通常用于将预先打开的文件 `stdin`、`stdout` 和 `stderr` 重定向到用户指定的文件。  与 `stream` 关联的新文件使用 `mode` 打开*，*所用的是指定文件要求的访问权限类型的字符串，如下所述：  
  
 `"r"`  
 打开以便读取。  如果文件不存在或找不到，`freopen_s` 调用将失败。  
  
 `"w"`  
 打开用于写入的空文件。  如果给定文件存在，则其内容会被销毁。  
  
 `"a"`  
 打开以在文件末尾进行写入（追加），在新数据写入到文件之前不移除 EOF 标记；如果文件不存在，则先创建文件。  
  
 `"r+"`  
 打开以便读取和写入。  （文件必须存在。）  
  
 `"w+"`  
 打开用于读取和写入的空文件。  如果给定文件存在，则其内容会被销毁。  
  
 `"a+"`  
 打开以进行读取和追加；追加操作包括在新数据写入到文件之前移除 EOF 标记并在写入完成后还原 EOF 标记；如果文件不存在，则先创建文件。  
  
 使用 `"w"` 和 `"w+"` 类型时要小心，因为它们可能会破坏现有文件。  
  
 使用 `"a"` 或 `"a+"` 访问类型打开文件时，所有写入操作均将在文件末尾进行。  虽然使用 `fseek` 或 `rewind` 可重新定位文件指针，但在执行任何写入操作前，文件指针将始终被移回文件末尾。  因此，无法覆盖现有数据。  
  
 在 EOF 标记追加到文件之前，`"a"` 模式不会将其移除。  在追加后，MS\-DOS TYPE 命令只显示原始 EOF 标记之前的数据，不显示追加到文件的任何数据。  在 EOF 标记追加到文件之前，`"a+"` 模式会将其移除。  在追加后，MS\-DOS TYPE 命令显示文件中的所有数据。  需使用 `"a+"` 模式才能附加到通过 CTRL\+Z EOF 标记终止的流文件。  
  
 指定 `"r+",`、`"w+",` 或 `"a+"` 访问类型时，允许读取和写入（文件将处于打开状态以进行“更新”）。  但是，在读取与写入之间切换时，必须有中间 [fsetpos](../../c-runtime-library/reference/fsetpos.md)、[fseek](../../c-runtime-library/reference/fseek-fseeki64.md) 或 [rewind](../../c-runtime-library/reference/rewind.md) 操作。  如果需要的话，可以为 `fsetpos` 或 `fseek` 操作指定当前位置。  除了以上值之外，还可以在 `mode` 字符串中包含以下字符之一以指定新行的转换模式。  
  
 `t`  
 在文本（已转换）模式下打开；输入时，回车\/换行 \(CR\-LF\) 组合将转换为单一的换行 \(LF\) 字符；输出时，LF 字符将转换为 CR\-LF 组合。  CTRL\+Z 也将在输入时解释为文件尾字符。  在打开以便利用 `"a+"` 进行读取或读写的文件中，运行时库将检查文件末尾的 CTRL\+Z 并在可能的情况下将其移除。  这是因为使用 `fseek` 和 `ftell` 在文件中移动时，可能导致 `fseek` 在文件末尾附近错误运行。  `t` 选项是一个 Microsoft 扩展，不应在需要 ANSI 可移植性的地方使用。  
  
 `b`  
 在二进制（未转换）模式下打开；会禁止上述的转换。  
  
 如果 `t` 或 `b` 在 `mode` 中未给出，则默认转换模式由全局变量 [\_fmode](../../c-runtime-library/fmode.md) 定义。  如果 `t` 或 `b` 是该参数的前缀，则函数将失败并返回 `NULL`。  
  
 有关文本和二进制模式的讨论，请参阅[文本和二进制模式文件 I\/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md)。  
  
## 要求  
  
|函数|必需的标头|  
|--------|-----------|  
|`freopen_s`|\<stdio.h\>|  
|`_wfreopen_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。  有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_freopen_s.c  
// This program reassigns stderr to the file  
// named FREOPEN.OUT and writes a line to that file.  
  
#include <stdio.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int main( void )  
{  
   errno_t err;  
   // Reassign "stderr" to "freopen.out":   
   err = freopen_s( &stream, "freopen.out", "w", stderr );  
  
   if( err != 0 )  
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
  
  **成功重新分配**  
**将转到文件“freopen.out”**   
## .NET Framework 等效项  
  
-   [System::IO::File::Open](https://msdn.microsoft.com/en-us/library/system.io.file.open.aspx)  
  
-   <xref:System.IO.FileStream.%23ctor%2A>  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [freopen、\_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)   
 [fclose、\_fcloseall](../../c-runtime-library/reference/fclose-fcloseall.md)   
 [\_fdopen、\_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [\_fileno](../../c-runtime-library/reference/fileno.md)   
 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [\_setmode](../../c-runtime-library/reference/setmode.md)