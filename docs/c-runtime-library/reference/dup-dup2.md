---
title: "_dup、_dup2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_dup"
  - "_dup2"
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
  - "_dup2"
  - "_dup"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_dup 函数"
  - "_dup2 函数"
  - "dup 函数"
  - "dup2 函数"
  - "文件句柄 [C++], 复制"
  - "文件句柄 [C++], 重新分配"
ms.assetid: 4d07e92c-0d76-4832-a770-dfec0e7a0cfa
caps.latest.revision: 19
caps.handback.revision: 17
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _dup、_dup2
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建打开文件 \(`_dup`\) 第二个文件描述符，或重新分配文件描述符 \(`_dup2`\)。  
  
## 语法  
  
```  
int _dup(   
   int fd   
);  
int _dup2(   
   int fd1,  
   int fd2   
);  
```  
  
#### 参数  
 `fd`, `fd1`  
 引用开启文件的描述符。  
  
 `fd2`  
 任何文件描述符。  
  
## 返回值  
 `_dup` 返回一个新文件描述符。  `_dup2` 返回 0 指示成功。  如果发生错误，每个函数返回– 1 并将 `errno` 设置到 `EBADF`，如果文件说明符无效或为 `EMFILE`，如果没有其他文件描述符不可用。  万一文件描述符无效，该函数调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_dup` 和 `_dup2` 函数关联当前打开的文件第二个文件描述符。  这些函数可用于将预定义的文件描述符，如 `stdout`，不同的文件。  使用任何一个文件描述符，文件中的操作可执行。  允许的文件访问的类型不受创建一个新的描述符影响。  `_dup` 返回特定文件的下一个可用的文件描述符。  `_dup2` 强制 `fd2` 引用和 `fd1`相同的文件。  如果 `fd2` 在调用时与打开文件关联，该文件已关闭。  
  
 `_dup` 和 `_dup2` 都接受文件描述符作为参数。  若要通过流 `(FILE *)` 到其中一种函数，请使用 [\_fileno](../../c-runtime-library/reference/fileno.md)。  `fileno` 实例准确的返回与当前特定流联系的文件描述符。  下面的示例演示如何将 `stderr` \(定义为 Stdio.h 的 `FILE` `*` \) 与文件描述符关联：  
  
```  
int cstderr = _dup( _fileno( stderr ));  
```  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_dup`|\<io.h\>|  
|`_dup2`|\<io.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_dup.c  
// This program uses the variable old to save  
// the original stdout. It then opens a new file named  
// DataFile and forces stdout to refer to it. Finally, it  
// restores stdout to its original state.  
//  
  
#include <io.h>  
#include <stdlib.h>  
#include <stdio.h>  
  
int main( void )  
{  
   int old;  
   FILE *DataFile;  
  
   old = _dup( 1 );   // "old" now refers to "stdout"   
                      // Note:  file descriptor 1 == "stdout"   
   if( old == -1 )  
   {  
      perror( "_dup( 1 ) failure" );  
      exit( 1 );  
   }  
   _write( old, "This goes to stdout first\n", 26 );  
   if( fopen_s( &DataFile, "data", "w" ) != 0 )  
   {  
      puts( "Can't open file 'data'\n" );  
      exit( 1 );  
   }  
  
   // stdout now refers to file "data"   
   if( -1 == _dup2( _fileno( DataFile ), 1 ) )  
   {  
      perror( "Can't _dup2 stdout" );  
      exit( 1 );  
   }  
   puts( "This goes to file 'data'\n" );  
  
   // Flush stdout stream buffer so it goes to correct file   
   fflush( stdout );  
   fclose( DataFile );  
  
   // Restore original stdout   
   _dup2( old, 1 );  
   puts( "This goes to stdout\n" );  
   puts( "The file 'data' contains:" );  
   _flushall();  
   system( "type data" );  
}  
```  
  
  **这首先转到 stdout**  
**这转到 stdout**  
**文件“数据”包含：**  
**这转到文件“数据”**   
## 请参阅  
 [低级别 I\/O](../../c-runtime-library/low-level-i-o.md)   
 [\_close](../../c-runtime-library/reference/close.md)   
 [\_creat、\_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)