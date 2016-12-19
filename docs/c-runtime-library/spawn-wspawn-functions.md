---
title: "_spawn, _wspawn 函数 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_spawn"
  - "_tspawnlp"
  - "_tspawnlpe"
  - "_tspawnve"
  - "_tspawnvp"
  - "_tspawnvpe"
  - "_tspawnl"
  - "spawn"
  - "_tspawnv"
  - "_tspawnle"
  - "wspawn"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_tspawnve 函数"
  - "_spawn 函数"
  - "_tspawnlpe 函数"
  - "tspawnvpe 函数"
  - "进程，正在创建"
  - "tspawnve 函数"
  - "_tspawnvp 函数"
  - "spawn 函数"
  - "tspawnl 函数"
  - "tspawnlp 函数"
  - "_tspawnvpe 函数"
  - "_tspawnl 函数"
  - "tspawnvp 函数"
  - "tspawnv 函数"
  - "进程，正在执行全新"
  - "_tspawnv 函数"
  - "tspawnle 函数"
  - "进程创建"
  - "_tspawnlp 函数"
  - "tspawnlpe 函数"
  - "_tspawnle 函数"
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _spawn, _wspawn 函数
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每个 `_spawn` 函数创建并执行更新过程：  
  
|||  
|-|-|  
|[\_spawnl、\_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[\_spawnv、\_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|  
|[\_spawnle、\_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[\_spawnve、\_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|  
|[\_spawnlp、\_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[\_spawnvp、\_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|  
|[\_spawnlpe、\_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[\_spawnvpe、\_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|  
  
 函数名结尾处的字母确定变体。  
  
 `e`  
 `envp`指向环境设置的数组指针，传递给新进程。  
  
 `l`  
 命令行声明被独自传送到 `_spawn` 函数.  当对更新过程的参数事先知道时通常使用该后缀。  
  
 `p`  
 这些函数使用 `PATH` 环境变量查找要执行的文件。  
  
 `v`  
 `argv`,命令行声明的数组指针被传递给 `_spawn`函数。  当对更新过程的参数是可变时使用该后缀。  
  
## 备注  
 `_spawn` 函数每个都创建并执行更新过程。  它们自动处理合适的多字节字符串参数，根据当前使用的多字节代码页识别多字节字符序列.  `_wspawn` 函数是 `_spawn` 函数的宽字符版本；不处理多字节字符字符串。  否则，`_wspawn` 函数具有相同的行为与其 `_spawn` 对等。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|  
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|  
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|  
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|  
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|  
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|  
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|  
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|  
  
 足够的内存必须可用提供用于加载和执行更新过程。  `mode` 参数以确定调用进程执行的操作在 `_spawn`的期间及之中。  以下 `mode` 的值在 Process.h 定义：  
  
 `_P_OVERLAY`  
 为更新覆盖一过程调用的过程，使用调用进程 \(作用与 `_exec` 调用相同\)。  
  
 `_P_WAIT`  
 挂起的调用线程，直至执行过程的更新完成 \(同步 `_spawn`\)。  
  
 `_P_NOWAIT` 或  `_P_NOWAITO`  
 继续在更新过程 \(异步 `_spawn`\) 的同时执行一个名为的进程。  
  
 `_P_DETACH`  
 继续执行调用进程；更新过程在后台运行没有到控制台或键盘的访问权限。  调用 `_cwait` 更新过程失败 \(异步 `_spawn`\)。  
  
 `cmdname` 执行参数指定的文件，当更新过程，并可以指定完整路径 \(从根\)，一部分路径 \(从当前工作目录\)，或文件名。  如果 `cmdname` 没有文件扩展名,在 \(.\)期间不结束，`_spawn` 函数先尝试 .com 文件扩展然后 .exe 文件扩展名、.bat 文件扩展名和最后 .cmd 文件扩展名。  
  
 如果 `cmdname` 具有文件扩展名，因此，只有使用该扩展。  如果 `cmdname` 在一段时期中结束, `_spawn` 函数不用文件扩展名搜索 `cmdname`。  `_spawnlp`, `_spawnlpe`, `_spawnvp` 和  `_spawnvpe` 搜索 `cmdname` \(使用相同步骤\) 在目录中由环境变量 `PATH`指定 .  
  
 如果 `cmdname` 包含一个驱动器符或任何斜线\(即如果这是相对路径\), `_spawn` 只对指定文件调用搜索; 路径没有搜索.  
  
 以前，其中数组大小为零。成功；函数 `errno` 当前行为是将 `errno` 触动越过在未成功，根据 C 标准。  如果需要模拟这一旧行为，调整 `errno` 为零在调用这些函数前面。  
  
> [!NOTE]
>  要确保正确的覆盖初始化和终止，请勿使用 `setjmp` 或 `longjmp` 函数进入或离开覆盖例程。  
  
## 为过程的参数  
 若要将参数传递以更新过程，请提供一个或多个字符串指针，`_spawn` 调用中参数。  这些字符串形式指定的进程的参数列表。  窗体更新过程的字符串的默认长度参数列表不能超过 1024 个字节。  终止 null 字符 \(“\\0 ”\) 每个字符串不包含在计数中，但是空格字符 \(自动插入分隔参数\) 包括在其中。  
  
> [!NOTE]
>  内嵌空格的字符串可能会导致意外的行为; 例如传递 `_spawn` 字符串 `"hi there"` 会导致新进程中获取两个参数, `"hi"` 和 `"there"`.  如果此语句的目的是让进程打开名为“hi there”的文件，这个进程将失败。  您可以通过引用字符串避免这种情况: `"\"hi there\""`.  
  
> [!IMPORTANT]
>  没有明确检查内容前不要将用户输入传递到 `_spawn` .  `_spawn` 会导致 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425) 调用，所以请记住不合格的路径名可能会导致潜在的安全漏洞.  
  
 可以将参数作为指针不同参数 \( `_spawnl`、`_spawnle`、`_spawnlp`和 `_spawnlpe`\) 或作为一组指针 \( `_spawnv`、`_spawnve`、`_spawnvp`和 `_spawnvpe`\)。  必须将至少一个参数、`arg0` 或 `argv`\[0\] 到指定的进程。  按照约定，因为您将键入对命令行，此参数是程序的名称。  \(其他值不会导致错误。\)  
  
 `_spawnl`、`_spawnle`、`_spawnlp`和 `_spawnlpe` 的参数数量调用，通常在预先知道的情况使用。  `arg0` 参数通常是指向 `cmdname`的指针。  参数`arg1` 通过指向字符串的 `argn`指针形成新的参数列表。  在 `argn` 之后，必须是一个 `NULL` 指针，用以标记参数列表的末尾。  
  
 在参数数目可变。更新过程时，`_spawnv`、`_spawnve`、`_spawnvp`和 `_spawnvpe` 调用是有用的。  指针参数被当作一个数组传递, `argv`*.*参数 `argv`\[0\] 通常是一个指向实际模式中的路径或保护模式中的程序的指针， `argv`\[1\] 通过 `argv`\[`n`\] 是指向形成新的参数列表的字符串的指针。  参数 `argv`\[`n` \+1\] 必须是一个 `NULL` 指针，用以标记参数列表的末尾。  
  
## 指定进程的环境  
 当调用 `_spawn` 时 空文件在新进程中继续为空.  在 `_spawnl`, `_spawnlp`, `_spawnv` 和 `_spawnvp` 调用中, 新进程继承调用进程的环境。  可以使用 `_spawnle`、`_spawnlpe`、`_spawnve`和 `_spawnvpe` 通过调用传递环境设置列表更新环境修改过程的 `envp` 参数。  `envp` 一个字符指针数组，该数组中的每个元素（除了最后一个元素）指向一个空结束的字符串，用于定义一个环境变量.  这样一个字符串通常有窗体 `NAME`\=`value` 当 `NAME` 是环境变量的名字且 `value` 是以该变量被设置的字符串值.\(注意 `value` 不括在双引号中。\)`envp` 的最后一个元素应为 `NULL`.  当 `envp` 是 `NULL`时, 引发的进程继承父进程的环境变量.  
  
 `_spawn` 函数可为更新过程传递关于文件打开的所有信息，包括特定模式。  此信息在实模式将 `C_FILE_INFO` 输入环境中。  启动代码通常处理此输入然后删除该环境。  但是，`_spawn`，则函数提供非 C 进程，此输入保持在环境中。  因为环境在实模式的信息传递，二进制格式打印环境本输入的定义字符串显示映射字符。  它不应具有影响行为的其他效果。  在内核模式，环境信息传递，文本形式而不包含映射字符。  
  
 你必须明确清除 \(using `fflush` 或 `_flushall`\) 或在 `_spawn` 函数调用前关闭任一流.  
  
 调用更新创建的过程到例程 `_spawn` 不会保留此设置。  而默认的生成处理状态重置信号设置。  
  
## 将输出重定向  
 如果调用从 DLL 或 GUI 应用程序的 `_spawn` \) 并希望重定向输出到管道，您有两个选择：  
  
-   使用 Win32 API 创建管道，然后调用 [AllocConsole](http://msdn.microsoft.com/library/windows/desktop/ms681944)，在结构和 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425)启动调用的句柄值。  
  
-   调用会创建管道的 [\_popen、\_wpopen](../c-runtime-library/reference/popen-wpopen.md) 和调用应用使用 **cmd.exe \/c** \(或 **command.exe \/c**\)。  
  
## 示例  
  
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
  
  **子进程输出**  
**from SPAWN\!**   
## 请参阅  
 [进程和环境控制](../c-runtime-library/process-and-environment-control.md)   
 [abort](../c-runtime-library/reference/abort.md)   
 [atexit](../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 函数](../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../c-runtime-library/reference/getmbcp.md)   
 [\_onexit、\_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../c-runtime-library/reference/setmbcp.md)   
 [system、\_wsystem](../c-runtime-library/reference/system-wsystem.md)