---
title: _CrtSetDbgFlag | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetDbgFlag
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
apitype: DLLExport
f1_keywords:
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 413504d8941aab1585ff03d361f8081fef4529a2
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetdbgflag"></a>_CrtSetDbgFlag

检索或修改 **_crtDbgFlag** 标志的状态，以控制调试堆管理器的分配行为（仅限调试版本）。

## <a name="syntax"></a>语法

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>参数

*newFlag*<br/>
**_crtDbgFlag** 的新状态。

## <a name="return-value"></a>返回值

返回之前的 **_crtDbgFlag** 状态。

## <a name="remarks"></a>备注

**_CrtSetDbgFlag**函数允许应用程序控制调试堆管理器如何跟踪通过修改的位域的内存分配 **_crtDbgFlag**标志。 通过设置位（打开），该应用程序可指示调试堆管理器执行特殊的调试操作，包括在应用程序退出时检查内存泄露并报告是否找到任何内存泄露、通过指定已释放的内存块应保留在堆的链接列表中来模拟内存不足情况，以及通过在每次分配请求时检查每个内存块来验证该堆的完整性。 当[_DEBUG](../../c-runtime-library/debug.md)未定义，则调用 **_CrtSetDbgFlag**在预处理过程中删除。

下表列出了 **_crtDbgFlag** 的位域并描述了其行为。 因为设置位将导致诊断输出增加、程序执行速度减慢，因此在默认情况下不会设置这些位（已关闭）。 有关这些位域的详细信息，请参阅[堆状态报告函数](/visualstudio/debugger/crt-debug-heap-details)。

|位域|默认|描述|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|打开|打开： 启用调试堆分配和使用的内存块类型标识符，例如 **_CLIENT_BLOCK**。 关闭：将新的分配添加到堆链接列表，但是将块类型设置为 **_IGNORE_BLOCK**。<br /><br /> 还可以与任何堆频率检查宏组合。|
|**_CRTDBG_CHECK_ALWAYS_DF**|关闭|打开：在每次分配和解除分配请求时调用 [_CrtCheckMemory](crtcheckmemory.md)。 OFF: **_CrtCheckMemory**必须显式调用。<br /><br /> 设置此标志后，堆频率检查宏不会产生任何影响。|
|**_CRTDBG_CHECK_CRT_DF**|关闭|打开： 包括 **_CRT_BLOCK**类型在泄漏检测和内存状态差异操作。 关闭：这些操作将忽略运行时库在内部使用的内存。<br /><br /> 还可以与任何堆频率检查宏组合。|
|**_CRTDBG_DELAY_FREE_MEM_DF**|关闭|打开：将已释放的内存块保留在堆链接列表中、向其分配 **_FREE_BLOCK** 类型，然后使用字节值 0xDD 进行填充。 关闭：不要将已释放的块保留在堆链接列表中。<br /><br /> 还可以与任何堆频率检查宏组合。|
|**_CRTDBG_LEAK_CHECK_DF**|关闭|打开：在程序退出时通过对 [_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md) 的调用执行自动泄露检查，如果应用程序无法释放它分配的所有内存，则生成错误报告。 关闭：不要在程序退出时自动执行泄露检查。<br /><br /> 还可以与任何堆频率检查宏组合。|

**堆频率检查宏**

你可以指定 C 运行时库执行的调试堆的验证的频率 (**_CrtCheckMemory**) 基于对的调用数**malloc**， **realloc**， **免费**，和 **_msize**。

**_CrtSetDbgFlag**然后检查的 16 位*newFlag*参数的值。 指定的值是数**malloc**， **realloc**，**免费**，和 **_msize**之间调用 **_CrtCheckMemory**调用。 为此，将提供四个预定义的宏。

|宏|对 _CrtCheckMemory 的调用之间的 malloc、realloc、free 和 _msize 调用数|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0（默认情况下，不存在堆检查）|

默认情况下， **_CrtCheckMemory**一旦调用每个 1,024 时间称为**malloc**， **realloc**，**免费**，和 **_msize**。

例如，可以指定 1 次堆检查每个 16 **malloc**， **realloc**，**免费**，和 **_msize**操作替换为以下代码：

```C
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

16 位*newFlag*指定 _CRTDBG_CHECK_ALWAYS_DF 时，将忽略参数。 在这种情况下， **_CrtCheckMemory**称为您每次调用**malloc**， **realloc**，**免费**，和 **_msize**.

*newFlag*是要应用于的新状态 **_crtDbgFlag** ，适用于每个位字段的值的组合。

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>更改一个或多个位域并创建标志的新状态

1. 调用 **_CrtSetDbgFlag**与*newFlag*等于 **_CRTDBG_REPORT_FLAG**以获取当前 **_crtDbgFlag**状态和存储在临时变量中的返回的值。

1. 打开任何位的按位**或**带相应位屏蔽 （在应用程序代码中由清单常量显示） 的临时变量。

1. 通过对带有相应位掩码的按位 **NOT** 的变量进行 **AND**-ing 运算关闭其他位。

1. 调用 **_CrtSetDbgFlag**与*newFlag*等于要设置的新状态的临时变量中存储的值 **_crtDbgFlag**。

下面的代码演示如何模拟内存不足条件通过让释放在堆链接列表中的内存块，并防止 **_CrtCheckMemory**在每个分配请求调用：

```C
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

有关内存管理和调试堆的概述，请参阅 [CRT 调试堆详细信息](/visualstudio/debugger/crt-debug-heap-details)。

若要禁用标志 **_CrtSetDbgFlag**函数，你应该**AND**的变量进行的按位**不**的位掩码。

如果*newFlag*不是有效的值，此函数将调用无效参数处理程序，如中所述[参数验证](../../c-runtime-library/parameter-validation.md)。 如果允许执行继续，此函数将**errno**到**EINVAL**并返回的前一状态 **_crtDbgFlag**。

## <a name="requirements"></a>要求

|例程|必需的标头|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>库

仅限 [C 运行时库](../../c-runtime-library/crt-library-features.md)的调试版本。

## <a name="example"></a>示例

```C
// crt_crtsetdflag.c
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug

// This program concentrates on allocating and freeing memory
// blocks to test the functionality of the _crtDbgFlag flag.

#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main( )
{
    char *p1, *p2;
    int tmpDbgFlag;

    _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );

    // Set the debug-heap flag to keep freed blocks in the
    // heap's linked list - This will allow us to catch any
    // inadvertent use of freed memory
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;
    tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Allocate 2 memory blocks and store a string in each
    p1 = malloc( 34 );
    p2 = malloc( 38 );
    strcpy_s( p1, 34, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 38, "p2 points to a Client allocation block" );

    // Free both memory blocks
    free( p2 );
    free( p1 );

    // Set the debug-heap flag to no longer keep freed blocks in the
    // heap's linked list and turn on Debug type allocations (CLIENT)
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;
    tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Explicitly call _malloc_dbg to obtain the filename and
    // line number of our allocation request and also so we can
    // allocate CLIENT type blocks specifically for tracking
    p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );
    p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );
    strcpy_s( p1, 40, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 40, "p2 points to a Client allocation block" );

    // _free_dbg must be called to free the CLIENT block
    _free_dbg( p2, _CLIENT_BLOCK );
    free( p1 );

    // Allocate p1 again and then exit - this will leave unfreed
    // memory on the heap
    p1 = malloc( 10 );
}
```

## <a name="see-also"></a>请参阅

[调试例程](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtCheckMemory](crtcheckmemory.md)<br/>
