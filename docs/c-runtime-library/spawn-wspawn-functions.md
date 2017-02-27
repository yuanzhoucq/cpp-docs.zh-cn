---
title: "_spawn、_wspawn 函数 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apilocation:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
dev_langs:
- C++
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 1794395cd9e6684788458aad424336efbc421c0a

---
# <a name="spawn-wspawn-functions"></a>_spawn、_wspawn 函数
每个 `_spawn` 函数将创建并执行一个新进程：  
  
|||  
|-|-|  
|[_spawnl、_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv、_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|  
|[_spawnle、_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve、_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|  
|[_spawnlp、_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp、_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|  
|[_spawnlpe、_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe、_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|  
  
 函数名称的结尾字母确定变体。  
  
 `e`  
指向环境设置的指针的数组  `envp` 将传递给新进程。  
  
 `l`  
 将命令行参数单独传递给 `_spawn` 函数。 一般将在预先知道新进程的一些参数时使用此后缀。  
  
 `p`  
 `PATH` 环境变量用于查找要执行的文件。  
  
 `v`  
指向命令行参数的指针的数组  `argv` 将传递给 `_spawn` 函数。 一般在新进程的一些参数可变时使用此后缀。  
  
## <a name="remarks"></a>备注  
 每个 `_spawn` 函数都将创建并执行一个新进程。 它们将根据情况自动处理多字节字符串参数，根据当前正在使用中的多字节代码页识别多字节字符序列。 `_wspawn` 函数是 `_spawn` 函数的宽字符版本；它们不处理多字节字符串。 否则，`_wspawn` 函数的行为将与其 `_spawn` 对等函数的一致。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|  
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|  
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|  
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|  
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|  
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|  
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|  
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|  
  
 加载和执行新进程必须有足够的内存可用。 `mode` 参数确定调用进程在 `_spawn` 之前以及期间将执行的操作。 `mode` 的下列值是在 Process.h 中定义的：  
  
 `_P_OVERLAY`  
 使用新进程覆盖调用进程，销毁调用进程（效果与 `_exec` 调用相同）。  
  
 `_P_WAIT`  
 在新进程执行完成之前挂起调用线程（同步 `_spawn`）。  
  
 `_P_NOWAIT` 或 `_P_NOWAITO`  
 继续与新进程一起并发执行调用进程（异步 `_spawn`）。  
  
 `_P_DETACH`  
 继续执行调用进程；新进程将在后台运行，而且不会访问控制台或键盘。 针对新进程调用 `_cwait` 将失败（异步 `_spawn`）。  
  
 `cmdname` 参数指定将作为新进程执行的文件，并可以指定完整路径（从根）、部分路径（从当前工作目录）或仅指定文件名。 如果 `cmdname` 没有文件扩展名或不是以句点 (.) 结尾的，则 `_spawn` 函数将先依次尝试 .com 文件扩展名、.exe 文件扩展名、.bat 文件扩展名和 .cmd 文件扩展名。  
  
 如果 `cmdname` 具有文件扩展名，则仅使用该扩展名。 如果 `cmdname` 以句点结尾，则 `_spawn` 调用将搜索不带文件扩展名的 `cmdname`。 `_spawnlp`、`_spawnlpe`、`_spawnvp` 和 `_spawnvpe` 函数将在 `PATH` 环境变量指定的目录中搜索 `cmdname`（使用相同过程）。  
  
 如果 `cmdname` 包含驱动器名或任何斜线（即，如果它是相对路径），则 `_spawn` 调用将仅搜索指定文件；不会执行路径搜索。  
  
 以前，这些函数中部分函数在成功时将 `errno` 设置为零；当前行为是在成功时保持不改动 `errno`，如 C 标准所指定。 如果需要模拟这一旧行为，请在调用这些函数之前将 `errno` 设置为零。  
  
> [!NOTE]
>  若要确保正确覆盖初始化和终止，请勿使用 `setjmp` 或 `longjmp` 函数进入或离开覆盖例程。  
  
## <a name="arguments-for-the-spawned-process"></a>生成进程的参数  
 若要将参数传递给新进程，请在 `_spawn` 调用中将一个或多个指向字符串的指针作为参数提供。 这些字符串构成了生成进程的参数列表。 构成新进程参数列表的字符串的组合长度不得超过 1024 个字节。 每个字符串的终止 null 字符 (“\0”) 不包含在计数中，但是空格字符（自动插入以分隔参数）包括在内。  
  
> [!NOTE]
>  嵌入字符串中的空格可能导致意外行为；例如，将字符串 `_spawn` 传递给 `"hi there"` 会导致新进程获得两个参数：`"hi"` 和 `"there"`。 如果想要让新进程打开名为“hi there”的文件，则该进程将失败。 你可以通过引用字符串 `"\"hi there\""` 来避免此问题。  
  
> [!IMPORTANT]
>  如果没有显式地检查其内容，请不要将用户输入传递给 `_spawn`。 `_spawn` 将导致调用 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425)，因此请牢记，未限定的路径名称可能会导致潜在的安全漏洞。  
  
 您可以将参数指针作为不同的参数传递（在 `_spawnl`、`_spawnle`、`_spawnlp` 和 `_spawnlpe` 中）或作为指针数组传递（在 `_spawnv`、`_spawnve`、`_spawnvp` 和 `_spawnvpe` 中）。 您必须至少将一个参数 `arg0` 或 `argv`[0] 传递到生成进程。 按照约定，此参数是程序的名称，因为您将在命令行上键入该名称。 不同的值不会生成错误。  
  
 一般将在提前知道参数数量的情况下使用 `_spawnl`、`_spawnle`、`_spawnlp` 和 `_spawnlpe` 调用。 `arg0` 参数通常是指向 `cmdname`的指针。 参数 `arg1` 到 `argn` 是指向构成新参数列表的字符字符串的指针。 在 `argn` 之后，必须是一个 `NULL` 指针，用以标记参数列表的末尾。  
  
 `_spawnv`、`_spawnve`、`_spawnvp` 和 `_spawnvpe` 调用在新进程具有数量可变的参数时很有用。 指向参数的指针将作为数组 `argv`* 传递。* 参数 `argv`[0] 通常是一个指向实际模式中的路径或保护模式中的程序的指针，从 `argv`[1] 到 `argv`[`n`] 都是指向构成新参数列表的字符串的指针。 参数 `argv`[`n` +1] 必须是一个 `NULL` 指针，用以标记参数列表的末尾。  
  
## <a name="environment-of-the-spawned-process"></a>生成进程的环境  
 调用 `_spawn` 时打开的文件在新进程中仍处于打开状态。 在 `_spawnl`、`_spawnlp`、`_spawnv` 和 `_spawnvp` 调用中，新进程将继承调用进程的环境。 您可以使用 `_spawnle`、`_spawnlpe`、`_spawnve` 和 `_spawnvpe` 调用更改新进程的环境，方式为通过 `envp` 参数传递环境设置的列表。 参数 `envp` 是字符指针的数组，其中每个元素（除了最后一个元素）均指向一个定义环境变量的不以 null 结尾的字符串。 此类字符串通常具有 `NAME`=`value` 格式，其中 `NAME` 是环境变量的名称，`value` 是为该变量设置的字符串值。 （请注意，`value` 并未括在双引号中。）`envp` 数组的最后一个元素应该是 `NULL`。 当 `envp` 本身为 `NULL` 时，生成进程将继承父进程的环境设置。  
  
 `_spawn` 函数可将所有有关打开的文件（包括转换模式）的信息传递到新进程。 此信息将在实模式下通过环境中的 `C_FILE_INFO` 条目传递。 启动代码通常会处理此条目，然后将其从环境中删除。 但是，如果 `_spawn` 函数生成一个非 C 进程，则此条目仍将保留在环境中。 打印环境将在此条目的定义字符串中显示图形字符，因为环境信息在实模式下是以二进制格式传递的。 它不应对正常操作具有任何其他影响。 在保护模式下，环境信息是以文本形式传递的，因此不包含图形字符。  
  
 在调用 `fflush` 函数之前，您必须显式刷新（使用 `_flushall` 或 `_spawn`）或关闭任何流。  
  
 通过调用 `_spawn` 例程创建的新进程不会保留任何信号设置。 而生成进程会将信号设置重置为默认值。  
  
## <a name="redirecting-output"></a>重定向输出  
 如果从 DLL 或 GUI 应用程序调用 `_spawn` 并希望将输出重定向至管道，则您具有两个选择：  
  
-   使用 Win32 API 创建管道，然后调用 [AllocConsole](http://msdn.microsoft.com/library/windows/desktop/ms681944)，在启动结构中设置句柄值，然后调用 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425)。  
  
-   调用 [_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md) 以创建管道，并使用 **cmd.exe /c**（或 **command.exe /c**）调用应用。  
  
## <a name="example"></a>示例  
  
```  
// crt_spawn.c  
// This program accepts a number in the range  
// 1-8 from the command line. Based on the number it receives,  
// it executes one of the eight different procedures that  
// spawn the process named child. For some of these procedures,  
// the CHILD.EXE file must be in the same directory; for  
// others, it only has to be in the same path.  
//  
  
#include <stdio.h>  
#include <process.h>  
  
char *my_env[] =  
{  
   "THIS=environment will be",  
   "PASSED=to child.exe by the",  
   "_SPAWNLE=and",  
   "_SPAWNLPE=and",  
   "_SPAWNVE=and",  
   "_SPAWNVPE=functions",  
   NULL  
};  
  
int main( int argc, char *argv[] )  
{  
   char *args[4];  
  
   // Set up parameters to be sent:   
   args[0] = "child";  
   args[1] = "spawn??";  
   args[2] = "two";  
   args[3] = NULL;  
  
   if (argc <= 2)  
   {  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
  
   switch (argv[1][0])   // Based on first letter of argument   
   {  
   case '1':  
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );  
      break;  
   case '2':  
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",   
               NULL, my_env );  
      break;  
   case '3':  
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );  
      break;  
   case '4':  
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",   
                NULL, my_env );  
      break;  
   case '5':  
      _spawnv( _P_OVERLAY, argv[2], args );  
      break;  
   case '6':  
      _spawnve( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   case '7':  
      _spawnvp( _P_OVERLAY, argv[2], args );  
      break;  
   case '8':  
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );  
      break;  
   default:  
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );  
      exit( 1 );  
   }  
   printf( "from SPAWN!\n" );  
}  
```  
  
```Output  
child process output  
from SPAWN!  
```  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../c-runtime-library/process-and-environment-control.md)   
 [abort](../c-runtime-library/reference/abort.md)   
 [atexit](../c-runtime-library/reference/atexit.md)   
 [_exec、_wexec 函数](../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../c-runtime-library/reference/flushall.md)   
 [_getmbcp](../c-runtime-library/reference/getmbcp.md)   
 [_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_setmbcp](../c-runtime-library/reference/setmbcp.md)   
 [system、_wsystem](../c-runtime-library/reference/system-wsystem.md)


<!--HONumber=Feb17_HO4-->


