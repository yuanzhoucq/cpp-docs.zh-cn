---
title: "_pipe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_pipe"
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
  - "pipe"
  - "_pipe"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_pipe 函数"
  - "pipe 函数"
  - "管道"
  - "管道, 创建"
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
caps.latest.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 20
---
# _pipe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建一个读写操作的管道。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
      int _pipe(  
int *pfds,  
unsigned int psize,  
int textmode   
);  
```  
  
#### 参数  
 `pfds`\[2\]  
 保存读写文件描述符的数组。  
  
 `psize`  
 大量保留的内存。  
  
 `textmode`  
 文件架构。  
  
## 返回值  
 如果成功，则返回0 。  返回–1 指示错误。  在错误方面，`errno` 设置为下列值之一：  
  
-   `EMFILE`，指示没有其他文件描述符可用。  
  
-   `ENFILE`，表示系统\-文件\-表格溢出。  
  
-   `EINVAL`指示数组 `pfds` 是 null 指针或一个无效值传递给了 `textmode` 。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `_pipe` 函数创建一个 *管道*，是一个人工 I\/O 通道程序使用可将信息传递到其他过程。  管道类似于文件，因为它有一个文件指针，一个文件描述符或两者都有，可使用标准库输入和输出函数读取或写入。  但是，管道不表示特定文件或设备。  相反，它表示独立于为程序自身内存和完全受控与操作系统控件的临时存储。  
  
 `_pipe` 类似于 `_open`，但打开读取和写入的管道并返回两个文件说明符而不是一个。  程序可以使用管道的两边或关闭不需要的一边。  例如，当它执行如 `PROGRAM1 | PROGRAM2`的命令时，窗口的命令处理器创建一个管道。  
  
 `PROGRAM1` 标准输出描述符附加到管道编写描述符。  `PROGRAM2` 标准输入说明符附加到管道的读取描述符。  这样就无需创建临时文件为其他程序传递信息。  
  
 `_pipe`函数对 `pfds` 自变量中的管道返回两个文件描述符。  元素 `pfds`\[0\] 包含读取描述符,元素 `pfds`\[1\] 包含编写描述符。  管道文件描述符与其他文件描述符使用方式一样。\(低级别输入和输出函数 `_read` 和 `_write` 可以读取和写入管道。\)检测关闭管道情况，检查返回字节读取数为0 的 `_read` 请求。  
  
 `psize` 自变量以字节为单位指定大量内存保留管道。  `textmode` 自变量为管道指定转换模式。  清单常数 `_O_TEXT` 指定文本转换，常量 `_O_BINARY` 指定二进制转换。\(为文本和二进制模式的说明参见 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md) 。\)如果自变量 `textmode` 是 0，`_pipe` 使用默认模式指定的默认转换模式变量 [\_fmode](../../c-runtime-library/fmode.md)。  
  
 在多线程程序中，未能锁定执行。  返回的文件说明符是新打开的，在 `_pipe` 调用完成后才能被线程引用。  
  
 若要使用 `_pipe` 函数进行父进程和子进程之间的通信，每个进程只能有一个在管道中打开的描述符。  描述符必须相反：如果父级已打开一读取描述符，则子级必须打开写描述符。  做这个的最简便方法就是 `OR` `|`\)`textmode`的 `_O_NOINHERIT` 标志。  然后，使用 `_dup` 或 `_dup2` 创建要传递给子管道描述符可继承的副本。  关闭原始描述符，然后大量产生子进程。  从派生调用返回，关闭父进程中的重复描述符。  有关详细信息，请参阅本文后面的示例2。  
  
 在 windows 操作系统中，当其所有描述符已关闭时管道就被销毁。\(如果管道上所有的读描述符已关闭，那么写入管道会导致错误。\)在管道上所有读写操作一直等到有足够数据或缓冲空间完成 I\/O 请求。  
  
## 要求  
  
|例程|必需的标头|可选标头|  
|--------|-----------|----------|  
|`_pipe`|\<io.h\>|\<fcntl.h\>,1 \<errno.h\>2|  
  
 1 为 `_O_BINARY` 和 `_O_TEXT` 定义。  
  
 2 `errno` 定义.  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例 1  
  
```  
// crt_pipe.c  
/* This program uses the _pipe function to pass streams of  
 * text to spawned processes.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <io.h>  
#include <fcntl.h>  
#include <process.h>  
#include <math.h>  
  
enum PIPES { READ, WRITE }; /* Constants 0 and 1 for READ and WRITE */  
#define NUMPROBLEM 8  
  
int main( int argc, char *argv[] )  
{  
  
   int fdpipe[2];  
   char hstr[20];  
   int pid, problem, c;  
   int termstat;  
  
   /* If no arguments, this is the spawning process */  
   if( argc == 1 )  
   {  
  
      setvbuf( stdout, NULL, _IONBF, 0 );  
  
      /* Open a set of pipes */  
      if( _pipe( fdpipe, 256, O_BINARY ) == -1 )  
          exit( 1 );  
  
      /* Convert pipe read descriptor to string and pass as argument   
       * to spawned program. Program spawns itself (argv[0]).  
       */  
      _itoa_s( fdpipe[READ], hstr, sizeof(hstr), 10 );  
      if( ( pid = _spawnl( P_NOWAIT, argv[0], argv[0],   
            hstr, NULL ) ) == -1 )  
          printf( "Spawn failed" );  
  
      /* Put problem in write pipe. Since spawned program is   
       * running simultaneously, first solutions may be done   
       * before last problem is given.  
       */  
      for( problem = 1000; problem <= NUMPROBLEM * 1000; problem += 1000)  
      {  
  
         printf( "Son, what is the square root of %d?\n", problem );  
         _write( fdpipe[WRITE], (char *)&problem, sizeof( int ) );  
  
      }  
  
      /* Wait until spawned program is done processing. */  
      _cwait( &termstat, pid, WAIT_CHILD );  
      if( termstat & 0x0 )  
         printf( "Child failed\n" );  
  
      _close( fdpipe[READ] );  
      _close( fdpipe[WRITE] );  
  
   }  
  
   /* If there is an argument, this must be the spawned process. */  
   else  
   {  
  
      /* Convert passed string descriptor to integer descriptor. */  
      fdpipe[READ] = atoi( argv[1] );  
  
      /* Read problem from pipe and calculate solution. */  
      for( c = 0; c < NUMPROBLEM; c++ )  
      {  
  
        _read( fdpipe[READ], (char *)&problem, sizeof( int ) );  
        printf( "Dad, the square root of %d is %3.2f.\n",  
                 problem, sqrt( ( double )problem ) );  
  
      }  
   }  
}  
```  
  
## 示例输出  
  
```  
Son, what is the square root of 1000?  
Son, what is the square root of 2000?  
Son, what iDad, the square root of 1000 is 31.62.  
Dad, the square root of 2000 is 44.72.  
s the square root of 3000?  
Dad, the square root of 3000 is 54.77.  
Son, what is the square root of 4000?  
Dad, the square root of 4000 is 63.25.  
Son, what is the square root of 5000?  
Dad, the square root of 5000 is 70.71.  
Son, what is the square root of 6000?  
SonDad, the square root of 6000 is 77.46.  
, what is the square root of 7000?  
Dad, the square root of 7000 is 83.67.  
Son, what is the square root of 8000?  
Dad, the square root of 8000 is 89.44.  
```  
  
## 示例 2  
 下面是一个基本的筛选器应用程序。  创建处理给定的应用程序的 stdout 到筛选器的一个管道之后为应用程序产生 crt\_pipe\_beeper，。  筛选器取消 ASCII 7 \(提示音\) 字符。  
  
```  
// crt_pipe_beeper.c  
  
#include <stdio.h>  
#include <string.h>  
  
int main()  
{  
   int   i;  
   for(i=0;i<10;++i)  
      {  
         printf("This is speaker beep number %d...\n\7", i+1);  
      }  
   return 0;  
}  
```  
  
 实际筛选器应用程序：  
  
```  
// crt_pipe_BeepFilter.C  
// arguments: crt_pipe_beeper.exe  
  
#include <windows.h>  
#include <process.h>  
#include <memory.h>  
#include <string.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
#define   OUT_BUFF_SIZE 512  
#define   READ_FD 0  
#define   WRITE_FD 1  
#define   BEEP_CHAR 7  
  
char szBuffer[OUT_BUFF_SIZE];  
  
int Filter(char* szBuff, ULONG nSize, int nChar)  
{  
   char* szPos = szBuff + nSize -1;  
   char* szEnd = szPos;  
   int nRet = nSize;  
  
   while (szPos > szBuff)  
   {  
      if (*szPos == nChar)  
         {  
            memmove(szPos, szPos+1, szEnd - szPos);  
            --nRet;  
         }  
      --szPos;  
   }  
   return nRet;  
}  
  
int main(int argc, char** argv)  
{  
   int nExitCode = STILL_ACTIVE;  
   if (argc >= 2)  
   {  
      HANDLE hProcess;  
      int fdStdOut;  
      int fdStdOutPipe[2];  
  
      // Create the pipe  
      if(_pipe(fdStdOutPipe, 512, O_NOINHERIT) == -1)  
         return   1;  
  
      // Duplicate stdout file descriptor (next line will close original)  
      fdStdOut = _dup(_fileno(stdout));  
  
      // Duplicate write end of pipe to stdout file descriptor  
      if(_dup2(fdStdOutPipe[WRITE_FD], _fileno(stdout)) != 0)  
         return   2;  
  
      // Close original write end of pipe  
      _close(fdStdOutPipe[WRITE_FD]);  
  
      // Spawn process  
      hProcess = (HANDLE)_spawnvp(P_NOWAIT, argv[1],   
       (const char* const*)&argv[1]);  
  
      // Duplicate copy of original stdout back into stdout  
      if(_dup2(fdStdOut, _fileno(stdout)) != 0)  
         return   3;  
  
      // Close duplicate copy of original stdout  
      _close(fdStdOut);  
  
      if(hProcess)  
      {  
         int nOutRead;  
         while   (nExitCode == STILL_ACTIVE)  
         {  
            nOutRead = _read(fdStdOutPipe[READ_FD],   
             szBuffer, OUT_BUFF_SIZE);  
            if(nOutRead)  
            {  
               nOutRead = Filter(szBuffer, nOutRead, BEEP_CHAR);  
               fwrite(szBuffer, 1, nOutRead, stdout);  
            }  
  
            if(!GetExitCodeProcess(hProcess,(unsigned long*)&nExitCode))  
               return 4;  
         }  
      }  
   }  
   return nExitCode;  
}  
```  
  
## Output  
  
```  
This is speaker beep number 1...  
This is speaker beep number 2...  
This is speaker beep number 3...  
This is speaker beep number 4...  
This is speaker beep number 5...  
This is speaker beep number 6...  
This is speaker beep number 7...  
This is speaker beep number 8...  
This is speaker beep number 9...  
This is speaker beep number 10...  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关详细信息，请参阅[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)