---
title: "system、_wsystem |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- system
- _wsystem
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tsystem
- _wsystem
dev_langs:
- C++
helpviewer_keywords:
- _wsystem function
- wsystem function
- tsystem function
- _tsystem function
- system function
- commands, executing
- command interpreter
ms.assetid: 7d3df2b6-f742-49ce-bf52-012b0aee3df5
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 3ce182dd28fa5af0fef9c2c51c14fc54aa5af972
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="system-wsystem"></a>system、_wsystem
执行命令。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
int system(  
   const char *command   
);  
int _wsystem(  
   const wchar_t *command   
);  
```  
  
#### <a name="parameters"></a>参数  
 `command`  
 要执行的命令。  
  
## <a name="return-value"></a>返回值  
 如果 `command` 为 `NULL`，并且找到命令解释器，则返回一个非零值。 如果未找到命令解释器，则返回 0 并将 `errno` 设置为 `ENOENT`。 如果 `command` 不为 `NULL`，则 `system` 返回由命令解释器返回的值。 仅当命令解释器返回值 0 时，它才会返回值 0。 返回值-1 指示错误，和`errno`设置为以下值之一︰  
  
 `E2BIG`  
 自变量列表（与系统相关）太大。  
  
 `ENOENT`  
 无法找到命令解释器。  
  
 `ENOEXEC`  
 由于格式无效，无法执行命令解释器文件。  
  
 `ENOMEM`  
 没有足够的内存可用于执行命令；或可用内存已损坏；或存在无效块，这表明进行调用的进程未正确进行分配。  
  
 有关这些返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlis 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `system` 函数将 `command` 传递给命令解释器，该解释器将字符串作为操作系统命令运行。 `system` 使用 `COMSPEC` 和 `PATH` 环境变量来定位命令解释器文件 CMD.exe。 如果 `command` 为 `NULL`，则该函数只检查命令解释器是否存在。  
  
 您必须通过使用 `fflush` 或 `_flushall` 进行显式清除，或者在调用 `system` 之前关闭所有的流。  
  
 `_wsystem` 是 `system` 的宽字符版本；`command` 的 `_wsystem` 参数是宽字符字符串。 否则这些函数具有相同行为。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_tsystem`|`system`|`system`|`_wsystem`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`system`|\<process.h> 或 \<stdlib.h>|  
|`_wsystem`|\<process.h> 或 \<stdlib.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 此示例使用 `system` 来键入一个文本文件。  
  
```  
// crt_system.c  
  
#include <process.h>  
  
int main( void )  
{  
   system( "type crt_system.txt" );  
}  
```  
  
## <a name="input-crtsystemtxt"></a>输入：crt_system.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>输出  
  
```  
Line one.  
Line two.  
```  
  
## <a name="see-also"></a>另请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_exec、_wexec 函数](../../c-runtime-library/exec-wexec-functions.md)   
 [exit、_Exit、_exit](../../c-runtime-library/reference/exit-exit-exit.md)   
 [_flushall](../../c-runtime-library/reference/flushall.md)   
 [_spawn、_wspawn 函数](../../c-runtime-library/spawn-wspawn-functions.md)
