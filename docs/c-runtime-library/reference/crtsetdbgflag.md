---
title: "_CrtSetDbgFlag | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_CrtSetDbgFlag"
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
apitype: "DLLExport"
f1_keywords: 
  - "_CRTDBG_REPORT_FLAG"
  - "_CRTDBG_CHECK_EVERY_16_DF"
  - "_CRTDBG_CHECK_DEFAULT_DF"
  - "CRTDBG_CHECK_DEFAULT_DF"
  - "CRTDBG_CHECK_EVERY_128_DF"
  - "CRTDBG_CHECK_EVERY_1024_DF"
  - "_CRTDBG_CHECK_EVERY_128_DF"
  - "CrtSetDbgFlag"
  - "CRTDBG_CHECK_EVERY_16_DF"
  - "_CRTDBG_CHECK_EVERY_1024_DF"
  - "_CrtSetDbgFlag"
  - "CRTDBG_REPORT_FLAG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRTDBG_ALLOC_MEM_DF 宏"
  - "_CRTDBG_CHECK_ALWAYS_DF 宏"
  - "_CRTDBG_CHECK_CRT_DF 宏"
  - "_CRTDBG_CHECK_DEFAULT_DF 宏"
  - "_CRTDBG_CHECK_EVERY_1024_DF 宏"
  - "_CRTDBG_CHECK_EVERY_128_DF 宏"
  - "_CRTDBG_CHECK_EVERY_16_DF 宏"
  - "_CRTDBG_DELAY_FREE_MEM_DF 宏"
  - "_CRTDBG_REPORT_FLAG 宏"
  - "_CrtSetDbgFlag 函数"
  - "CRTDBG_ALLOC_MEM_DF 宏"
  - "CRTDBG_CHECK_ALWAYS_DF 宏"
  - "CRTDBG_CHECK_CRT_DF 宏"
  - "CRTDBG_CHECK_DEFAULT_DF 宏"
  - "CRTDBG_CHECK_EVERY_1024_DF 宏"
  - "CRTDBG_CHECK_EVERY_128_DF 宏"
  - "CRTDBG_CHECK_EVERY_16_DF 宏"
  - "CRTDBG_DELAY_FREE_MEM_DF 宏"
  - "CRTDBG_REPORT_FLAG 宏"
  - "CrtSetDbgFlag 函数"
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# _CrtSetDbgFlag
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检索或修改 **\_crtDbgFlag** 标志的状态，以控制调试堆管理器的分配行为（仅限调试版本）。  
  
## 语法  
  
```  
  
int _CrtSetDbgFlag(     int newFlag  );  
```  
  
#### 参数  
 `newFlag`  
 **\_crtDbgFlag** 的新状态。  
  
## 返回值  
 返回之前的 **\_crtDbgFlag** 状态。  
  
## 备注  
 `_CrtSetDbgFlag` 函数允许应用程序通过修改 **\_crtDbgFlag** 标志的位域，来控制调试堆管理器跟踪内存分配的方式。  通过设置位（打开），该应用程序可指示调试堆管理器执行特殊的调试操作，包括在应用程序退出时检查内存泄露并报告是否找到任何内存泄露、通过指定已释放的内存块应保留在堆的链接列表中来模拟内存不足情况，以及通过在每次分配请求时检查每个内存块来验证该堆的完整性。  未定义 [\_DEBUG](../../c-runtime-library/debug.md) 时，将在预处理过程中删除对 `_CrtSetDbgFlag` 的调用。  
  
 下表列出了 **\_crtDbgFlag** 的位域并描述了其行为。  因为设置位将导致诊断输出增加、程序执行速度减慢，因此在默认情况下不会设置这些位（已关闭）。  有关这些位域的详细信息，请参阅[堆状态报告函数](../Topic/CRT%20Debug%20Heap%20Details.md#BKMK_Heap_State_Reporting_Functions)。  
  
|位域|默认|描述|  
|--------|--------|--------|  
|**\_CRTDBG\_ALLOC\_MEM\_DF**|打开|打开：启用调试堆分配并使用内存块类型标识符，例如 `_CLIENT_BLOCK`。  关闭：将新的分配添加到堆链接列表，但是将块类型设置为 **\_IGNORE\_BLOCK**。<br /><br /> 还可以与任何堆频率检查宏组合。|  
|**\_CRTDBG\_CHECK\_ALWAYS\_DF**|关闭|打开：在每次分配和解除分配请求时调用 [\_CrtCheckMemory](../../c-runtime-library/reference/crtcheckmemory.md)。  关闭：必须显式调用 `_CrtCheckMemory`。<br /><br /> 设置此标志后，堆频率检查宏不会产生任何影响。|  
|`_CRTDBG_CHECK_CRT_DF`|关闭|打开：包括泄漏检测和内存状态差异操作中的 `_CRT_BLOCK` 类型。  关闭：这些操作将忽略运行时库在内部使用的内存。<br /><br /> 还可以与任何堆频率检查宏组合。|  
|**\_CRTDBG\_DELAY\_FREE\_MEM\_DF**|关闭|打开：将已释放的内存块保留在堆链接列表中、向其分配 **\_FREE\_BLOCK** 类型，然后使用字节值 0xDD 填充它们。  关闭：不要将已释放的块保留在堆链接列表中。<br /><br /> 还可以与任何堆频率检查宏组合。|  
|`_CRTDBG_LEAK_CHECK_DF`|关闭|打开：在程序退出时通过对 [\_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md) 的调用执行自动泄露检查，如果应用程序无法释放它分配的所有内存，则生成错误报告。  关闭：不要在程序退出时自动执行泄露检查。<br /><br /> 还可以与任何堆频率检查宏组合。|  
  
 **堆频率检查宏**  
  
 你可以根据对 `malloc`、`realloc`、**free** 和 `_msize` 的调用数，指定 C 运行时库执行调试堆 \(`_CrtCheckMemory`\) 验证的频率。  
  
 然后，`_CrtSetDbgFlag` 将检查某个值的 `newFlag` 参数较高的 16 位。  指定的值是 `_CrtCheckMemory` 调用之间的 `malloc`、`realloc`、**free** 和 `_msize` 调用数。  为此，将提供四个预定义的宏。  
  
|宏|对 \_CrtCheckMemory 的调用之间的 malloc、realloc、free 和 \_msize 调用数|  
|-------|-----------------------------------------------------------------|  
|\_CRTDBG\_CHECK\_EVERY\_16\_DF|16|  
|\_CRTDBG\_CHECK\_EVERY\_128\_DF|128|  
|\_CRTDBG\_CHECK\_EVERY\_1024\_DF|1024|  
|\_CRTDBG\_CHECK\_DEFAULT\_DF|0（默认情况下，不存在堆检查）|  
  
 默认情况下，每调用 1,024 次 `malloc`、`realloc`、**free** 和 `_msize`，将调用 1 次 `_CrtCheckMemory`。  
  
 例如，你可以使用以下代码指定每隔 16 个 `malloc`、`realloc`、**free** 和 `_msize` 操作执行 1 次堆检查：  
  
```  
#include <crtdbg.h>  
int main( )  
{  
int tmp;  
  
// Get the current bits  
tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
  
// Clear the upper 16 bits and OR in the desired freqency  
tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;  
  
// Set the new bits  
_CrtSetDbgFlag(tmp);  
}  
```  
  
 在指定 \_CRTDBG\_CHECK\_ALWAYS\_DF 时，忽略 `newFlag` 参数较高的 16 位。  在这种情况下，每次调用 `malloc`、`realloc`、**free** 和 `_msize` 时，都将调用 `_CrtCheckMemory`。  
  
 `newFlag` 是要应用到 **\_crtDbgFlag** 的新状态，也是每个位域的值的组合。  
  
### 更改一个或多个位域并创建标志的新状态  
  
1.  在 `newFlag` 等于 `_CRTDBG_REPORT_FLAG` 的情况下，调用 `_CrtSetDbgFlag` 获取当前的 **\_crtDbgFlag** 状态，并在一个临时变量中存储返回值。  
  
2.  通过对带有相应位掩码的临时变量（在应用程序代码中由清单常量显示）进行 `OR` 运算来打开任何位。  
  
3.  通过对带有相应位掩码的按位 **NOT** 的变量进行 **AND**\-ing 运算关闭其他位。  
  
4.  在 `newFlag` 等于临时变量中存储的值的情况下，调用 `_CrtSetDbgFlag` 以设置 **\_crtDbgFlag** 的新状态。  
  
 以下代码演示如何通过在堆链接列表中保留已释放的内存块来模拟内存不足情况，以及如何阻止在每个分配请求时都调用 `_CrtCheckMemory`：  
  
```  
// Get the current state of the flag  
// and store it in a temporary variable  
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );  
  
// Turn On (OR) - Keep freed memory blocks in the  
// heap's linked list and mark them as freed  
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;  
  
// Turn Off (AND) - prevent _CrtCheckMemory from  
// being called at every allocation request  
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;  
  
// Set the new state for the flag  
_CrtSetDbgFlag( tmpFlag );  
```  
  
 有关内存管理和调试堆的概述，请参阅 [CRT 调试堆详细信息](../Topic/CRT%20Debug%20Heap%20Details.md)。  
  
 若要使用 `_CrtSetDbgFlag` 函数禁用标志，你应该对带有位掩码的按位 **NOT** 的变量进行 **AND** 运算。  
  
 如果 `newFlag` 不是一个有效值，则此函数调用的参数处理程序无效，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则该函数会将 `errno` 设置为 `EINVAL` 并返回之前的 `_crtDbgFlag` 状态。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_CrtSetDbgFlag`|\<crtdbg.h\>|  
  
 有关更多兼容性信息，请参见“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。  
  
## 示例  
  
```  
// crt_crtsetdflag.c  
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug  
/*  
 * This program concentrates on allocating and freeing memory  
 * blocks to test the functionality of the _crtDbgFlag flag..  
 */  
  
#include <string.h>  
#include <malloc.h>  
#include <crtdbg.h>  
  
int main( )  
{  
        char *p1, *p2;  
        int tmpDbgFlag;  
  
        _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );  
        _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );  
        /*  
         * Set the debug-heap flag to keep freed blocks in the  
         * heap's linked list - This will allow us to catch any  
         * inadvertent use of freed memory  
         */  
        tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
        tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;  
        tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;  
        _CrtSetDbgFlag(tmpDbgFlag);  
  
        /*  
         * Allocate 2 memory blocks and store a string in each  
         */  
        p1 = malloc( 34 );  
        p2 = malloc( 38 );  
        strcpy_s( p1, 34, "p1 points to a Normal allocation block" );  
        strcpy_s( p2, 38, "p2 points to a Client allocation block" );  
  
        /*  
         * Free both memory blocks  
         */  
        free( p2 );  
        free( p1 );  
  
        /*  
         * Set the debug-heap flag to no longer keep freed blocks in the  
         * heap's linked list and turn on Debug type allocations (CLIENT)  
         */  
        tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);  
        tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;  
        tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;  
        _CrtSetDbgFlag(tmpDbgFlag);  
  
        /*  
         * Explicitly call _malloc_dbg to obtain the filename and   
         * line number of our allocation request and also so we can   
         * allocate CLIENT type blocks specifically for tracking  
         */  
        p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );  
        p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );  
        strcpy_s( p1, 40, "p1 points to a Normal allocation block" );  
        strcpy_s( p2, 40, "p2 points to a Client allocation block" );  
  
        /*  
         * _free_dbg must be called to free the CLIENT block  
         */  
        _free_dbg( p2, _CLIENT_BLOCK );  
        free( p1 );  
  
        /*  
         * Allocate p1 again and then exit - this will leave unfreed  
         * memory on the heap  
         */  
        p1 = malloc( 10 );  
}  
```  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [调试例程](../../c-runtime-library/debug-routines.md)   
 [\_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)   
 [\_CrtCheckMemory](../../c-runtime-library/reference/crtcheckmemory.md)