---
title: _exec、_wexec 函数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
dev_langs:
- C++
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1da7c4102f15bf4a9c8ec583cf39e621d6872cb0
ms.sourcegitcommit: b92ca0b74f0b00372709e81333885750ba91f90e
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/16/2018
ms.locfileid: "42578441"
---
# <a name="exec-wexec-functions"></a>_exec、_wexec 函数
此系列中的每个函数都会加载并执行新进程：  
  
|||  
|-|-|  
|[_execl、_wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv、_wexecv](../c-runtime-library/reference/execv-wexecv.md)|  
|[_execle、_wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve、_wexecve](../c-runtime-library/reference/execve-wexecve.md)|  
|[_execlp、_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp、_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|  
|[_execlpe、_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe、_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|  
  
 函数名称末尾的字母可确定该变量。  
  
|_exec 函数后缀|描述|  
|----------------------------|-----------------|  
|`e`|将指向环境设置的指针数组 `envp` 传递给新进程。|  
|`l`|将命令行参数单独传递给 `_exec` 函数。 通常在提前知道新进程的参数数量时使用。|  
|`p`|`PATH` 环境变量用于查找要执行的文件。|  
|`v`|将指向命令行参数的指针数组 `argv` 传递给 `_exec`。 通常在新进程的参数数量可变时使用。|  
  
## <a name="remarks"></a>备注  
 每个 `_exec` 函数都会加载并执行新进程。 所有 `_exec` 函数均使用同一个操作系统函数 ([CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa))。 `_exec` 函数将适当自动处理多字节字符字符串参数，从而根据当前正在使用的多字节代码页识别多字节字符序列。 `_wexec` 函数是 `_exec` 函数的宽字符版本。 `_wexec` 函数的行为与其对应系列 `_exec` 完全相同，差别在于这些函数不处理多字节字符字符串。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_texecl`|`_execl`|`_execl`|`_wexecl`|  
|`_texecle`|`_execle`|`_execle`|`_wexecle`|  
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|  
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|  
|`_texecv`|`_execv`|`_execv`|`_wexecv`|  
|`_texecve`|`_execve`|`_execve`|`_wexecve`|  
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|  
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|  
  
 `cmdname` 参数指定要作为新进程执行的文件。 它可指定完整路径（来自根）、部分路径（来自当前工作目录）或文件名。 如果 `cmdname` 不具有文件扩展名或不以句点 (.) 结尾，则 `_exec` 函数将搜索已命名的文件。 如果搜索未成功，则它将尝试使用与 .com 文件扩展名相同的基名称，然后依次使用与 .exe、.bat 和 .cmd 文件扩展名相同的基名称。 如果 `cmdname` 具有文件扩展名，则仅在搜索中使用该扩展名。 如果 `cmdname` 以句点结尾，则 `_exec` 函数将搜索不具有文件扩展名的 `cmdname`。 `_execlp`、`_execlpe`、`_execvp` 和 `_execvpe` 将在由 `cmdname` 环境变量指定的目录中（使用相同过程）搜索 `PATH`。 如果 `cmdname` 包含一个驱动器说明符或任何斜杠（即如果它是相对路径），则 `_exec` 将仅调用对指定文件的搜索；不会搜索该路径。  
  
 通过将一个或多个指向字符字符串的指针给定为 `_exec` 调用中的参数，将参数传递给新进程。 这些字符字符串将构成该新进程的参数列表。 继承的环境设置和构成新进程参数列表的字符串的组合长度不能超过 32 KB。 计数中不包括每个字符串的以 null 结尾的字符 ('\0')，但是会计入空格字符（自动插入以分隔参数）。  
  
> [!NOTE]
>  嵌入字符串中的空格可能导致意外行为；例如，将字符串 `_exec` 传递给 `"hi there"` 会导致新进程获得两个参数：`"hi"` 和 `"there"`。 如果想要让新进程打开名为“hi there”的文件，则该进程将失败。 你可以通过引用字符串 `"\"hi there\""` 来避免此问题。  
  
> [!IMPORTANT]
>  如果没有显式地检查其内容，请不要将用户输入传递给 `_exec`。 `_exec` 将导致调用 [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa)，因此请牢记，未限定的路径名称可能会导致潜在的安全漏洞。  
  
 `_exec` 函数将验证其参数。 如果预期参数是空指针、空字符串或省略了预期参数，则 `_exec` 函数调用的参数处理程序无效，如[参数验证](../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 -1。 不执行任何新进程。  
  
 可将参数指针作为单独参数进行传递（在 `_execl`、`_execle`、`_execlp` 和 `_execlpe` 中），或作为指针数组进行传递（在 `_execv`、`_execve`、`_execvp` 和 `_execvpe` 中）。 必须将至少一个参数 `arg0` 传递给新进程；此参数是该新进程的 `argv`[0]。 通常，此参数是 `cmdname` 的副本。 （不同的值不会产生错误。）  
  
 通常在提前知道参数数量时使用 `_execl`、`_execle`、`_execlp` 和 `_execlpe` 调用。 参数 `arg0` 通常是一个指向 `cmdname` 的指针。 参数 `arg1` 到 `argn` 指向构成新参数列表的字符字符串。 空指针必须在 `argn` 后才能标记参数列表的末尾。  
  
 `_execv`、`_execve`、`_execvp` 和 `_execvpe` 调用在新进程的参数数量可变时很有用。 将指向参数的指针作为数组 `argv` 进行传递。 参数 `argv`[0] 通常是一个指向 `cmdname` 的指针。 参数 `argv`[1] 到 `argv`[`n`] 指向构成新参数列表的字符字符串。 参数 `argv`[`n`+1] 必须是一个 NULL 指针，用以标记参数列表的末尾。  
  
 在进行 `_exec` 调用时打开的文件在新进程中仍然保持打开状态。 在 `_execl`、`_execlp`、`_execv` 和 `_execvp` 调用中，新进程将继承调用进程的环境。 通过 `_execle` 参数传递环境设置的列表，`_execlpe`、`_execve`、`_execvpe` 和 `envp` 调用可更改新进程的环境。 `envp` 是一个字符指针数组，其中每个元素（最后一个元素除外）均指向定义环境变量的以 null 结尾的字符串。 此类字符串通常具有 `NAME`=`value` 格式，其中 `NAME` 是环境变量的名称，`value` 是为该变量设置的字符串值。 （请注意，`value` 并未括在双引号中。）`envp` 数组的最后一个元素应该是 NULL。 当 `envp` 本身是 NULL 时，新进程将继承调用进程的环境设置。  
  
 使用一个 `_exec` 函数执行的程序将始终加载到内存中，如同已将该程序的 .exe 文件头中的最大分配字段设置为默认值 0xFFFFH。  
  
 `_exec` 调用不会保留打开的文件的转换模式。 如果新进程必须使用继承自调用进程的文件，请使用 [_setmode](../c-runtime-library/reference/setmode.md) 例程将这些文件的转换模式设置为所需模式。 在 `fflush` 函数调用之前，你必须（使用 `_flushall` 或 `_exec`）显式刷新或关闭任何流。 信号设置不会保留在通过对 `_exec` 例程的调用而创建的新进程中。 会在新进程中将信号设置重置为默认设置。  
  
## <a name="example"></a>示例  
  
```  
// crt_args.c  
// Illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
// This program will be executed by crt_exec which follows.  
  
#include <stdio.h>  
  
int main( int argc,  // Number of strings in array argv  
 char *argv[],       // Array of command-line argument strings  
 char **envp )       // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.   
    printf( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
 运行以下程序以执行 Crt_args.exe：  
  
```  
// crt_exec.c  
// Illustrates the different versions of exec, including  
//      _execl          _execle          _execlp          _execlpe  
//      _execv          _execve          _execvp          _execvpe  
//  
// Although CRT_EXEC.C can exec any program, you can verify how   
// different versions handle arguments and environment by   
// compiling and specifying the sample program CRT_ARGS.C. See   
// "_spawn, _wspawn Functions" for examples of the similar spawn   
// functions.  
  
#include <stdio.h>  
#include <conio.h>  
#include <process.h>  
  
char *my_env[] =     // Environment for exec?e  
{  
   "THIS=environment will be",  
   "PASSED=to new process by",  
   "the EXEC=functions",  
   NULL  
};  
  
int main( int ac, char* av[] )  
{  
   char *args[4];  
   int ch;  
   if( ac != 3 ){  
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );  
      return;  
   }  
  
   // Arguments for _execv?   
   args[0] = av[1];  
   args[1] = "exec??";  
   args[2] = "two";  
   args[3] = NULL;  
  
   switch( atoi( av[2] ) )  
   {  
   case 1:  
      _execl( av[1], av[1], "_execl", "two", NULL );  
      break;  
   case 2:  
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );  
      break;  
   case 3:  
      _execlp( av[1], av[1], "_execlp", "two", NULL );  
      break;  
   case 4:  
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );  
      break;  
   case 5:  
      _execv( av[1], args );  
      break;  
   case 6:  
      _execve( av[1], args, my_env );  
      break;  
   case 7:  
      _execvp( av[1], args );  
      break;  
   case 8:  
      _execvpe( av[1], args, my_env );  
      break;  
   default:  
      break;  
   }  
  
   // This point is reached only if exec fails.   
   printf( "\nProcess was not execed." );  
   exit( 0 );  
}  
```  
  
## <a name="requirements"></a>要求  
  
 **标头：** process.h  
  
## <a name="see-also"></a>请参阅  
 [进程和环境控制](../c-runtime-library/process-and-environment-control.md)   
 [abort](../c-runtime-library/reference/abort.md)   
 [atexit](../c-runtime-library/reference/atexit.md)   
 [exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [_spawn、_wspawn 函数](../c-runtime-library/spawn-wspawn-functions.md)   
 [system、_wsystem](../c-runtime-library/reference/system-wsystem.md)