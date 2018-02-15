---
title: "_setmode | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _setmode
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
- _setmode
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], console output
- files [C++], modes
- _setmode function
- file translation [C++], setting mode
- files [C++], translation
- setmode function
ms.assetid: 996ff7cb-11d1-43f4-9810-f6097182642a
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1d98825dfa2cbe6a38fc945fa9cfaaca4679cdb8
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="setmode"></a>_setmode
设置文件转换模式。  
  
## <a name="syntax"></a>语法  
  
```  
int _setmode (  
   int fd,  
   int mode   
);  
```  
  
#### <a name="parameters"></a>参数  
 `fd`  
 文件描述符。  
  
 `mode`  
 新转换模式。  
  
## <a name="return-value"></a>返回值  
 如果成功，将返回之前的转换模式。  
  
 如果传递到此函数的参数无效，则将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，此函数将返回-1 并设置`errno`为`EBADF`，指示无效文件描述符或`EINVAL`，指示无效`mode`自变量。  
  
 有关这些属性和其他的更多信息返回代码示例，请参见 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_setmode` 函数将 `mode` 设置为由 `fd` 给定的文件的转换模式。 通过将 `_O_TEXT` 传递为 `mode` 可设置文本（即转换）模式。 回车符返回行的源 (CR-LF) 组合将转换为单个换行符字符输入。 输出时换行符将转换为 CR-LF 组合。 传递 `_O_BINARY` 可设置二进制（未转换）模式，在该模式下会禁止这些转换。  
  
 你还可以传递`_O_U16TEXT`， `_O_U8TEXT`，或`_O_WTEXT`若要启用 Unicode 模式，如本文档后面的第二个示例中所示。 `_setmode` 通常用于修改 `stdin` 和 `stdout` 的默认转换模式，但是你可以在任何文件上使用它。 如果将 `_setmode` 应用到流的文件描述符中，则先调用 `_setmode`，然后再在该流上执行任何输入或输出操作。  
  
> [!CAUTION]
>  如果将数据写入文件流，请先通过使用 [fflush](../../c-runtime-library/reference/fflush.md) 显式刷新代码，然后再使用 `_setmode` 更改该模式。 如果不刷新代码，可能会导致意外行为。 如果尚未将数据写入流，则不必刷新代码。  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|可选标头|  
|-------------|---------------------|----------------------|  
|`_setmode`|\<io.h>|\<fcntl.h>|  
  
 有关更多兼容性信息，请参阅 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_setmode.c  
// This program uses _setmode to change  
// stdin from text mode to binary mode.  
  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
int main( void )  
{  
   int result;  
  
   // Set "stdin" to have binary mode:  
   result = _setmode( _fileno( stdin ), _O_BINARY );  
   if( result == -1 )  
      perror( "Cannot set mode" );  
   else  
      printf( "'stdin' successfully changed to binary mode\n" );  
}  
```  
  
```Output  
'stdin' successfully changed to binary mode  
```  
  
## <a name="example"></a>示例  
  
```  
// crt_setmodeunicode.c  
// This program uses _setmode to change  
// stdout to Unicode. Cyrillic and Ideographic  
// characters will appear on the console (if  
// your console font supports those character sets).  
  
#include <fcntl.h>  
#include <io.h>  
#include <stdio.h>  
  
int main(void) {  
    _setmode(_fileno(stdout), _O_U16TEXT);  
    wprintf(L"\x043a\x043e\x0448\x043a\x0430 \x65e5\x672c\x56fd\n");  
    return 0;  
}  
```  
  
## <a name="see-also"></a>请参阅  
 [文件处理](../../c-runtime-library/file-handling.md)   
 [_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_set_fmode](../../c-runtime-library/reference/set-fmode.md)