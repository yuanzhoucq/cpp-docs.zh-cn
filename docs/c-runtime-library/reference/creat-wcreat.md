---
title: "_creat、_wcreat | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _creat
- _wcreat
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
- wcreat
- _wcreat
- _creat
- tcreat
- _tcreat
dev_langs:
- C++
helpviewer_keywords:
- wcreat function
- _wcreat function
- files [C++], creating
- _creat function
- tcreat function
- creat function
- _tcreat function
ms.assetid: 3b3b795d-1620-40ec-bd2b-a4bbb0d20fe5
caps.latest.revision: 21
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: f034e2b80cc1bd3e7b5fc4578a6f5e77a060593c
ms.contentlocale: zh-cn
ms.lasthandoff: 04/01/2017

---
# <a name="creat-wcreat"></a>_creat、_wcreat
新建文件。 `_creat` 和 `_wcreat` 已弃用；请改用 [_sopen_s、_wsopen_s](../../c-runtime-library/reference/sopen-s-wsopen-s.md)。  
  
## <a name="syntax"></a>语法  
  
```  
int _creat(   
   const char *filename,  
   int pmode   
);  
int _wcreat(   
   const wchar_t *filename,  
   int pmode   
);  
```  
  
#### <a name="parameters"></a>参数  
 `filename`  
 新文件的名称。  
  
 `pmode`  
 权限设置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则这些函数将文件描述符返回到已创建文件。 否则，函数返回-1 并设置`errno`下表中所示。  
  
|`errno` 设置|描述|  
|---------------------|-----------------|  
|`EACCES`|`filename` 指定一个现有的只读文件或指定目录来代替某个文件。|  
|`EMFILE`|没有更多可用的文件描述符。|  
|`ENOENT`|找不到指定的文件。|  
  
 如果 `filename` 为 NULL，这些函数则会调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL` 并返回 -1。  
  
 有关这些代码及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `_creat` 函数创建一个新文件或打开并截断现有文件。 `_wcreat` 是 `_creat` 的宽字符版本；`filename` 的 `_wcreat` 参数是宽字符字符串。 除此以外，`_wcreat` 和 `_creat` 的行为完全相同。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|Tchar.h 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcreat`|`_creat`|`_creat`|`_wcreat`|  
  
 如果由 `filename` 指定的文件不存在，则创建具有给定权限设置的新文件并将其打开以供写入。 如果该文件已存在，且其权限设置允许写入，则 `_creat` 将文件长度截断为 0、销毁以前的内容并将其打开以供写入。 权限设置 `pmode` 仅适用于新创建的文件。 新文件第一次关闭后收到指定的权限设置。 整数表达式 `pmode` 包含在 SYS\Stat.h 中定义的 `_S_IWRITE` 和 `_S_IREAD` 清单常量中的一个或两个。 当给定这两个常量时，将使用按位 `OR` 运算符连接它们 ( **&#124;** )。 `pmode` 参数可设置为下列值之一。  
  
|值|定义|  
|-----------|----------------|  
|`_S_IWRITE`|允许写入。|  
|`_S_IREAD`|允许读取。|  
|`_S_IREAD &#124; _S_IWRITE`|允许读取和写入。|  
  
 如果未授予写入权限，则该文件为只读。 所有文件始终具有可读性；不能提供只写权限。 模式 `_S_IWRITE` 和 `_S_IREAD | _S_IWRITE` 是等效的。 使用 `_creat` 打开的文件始终在 `_SH_DENYNO` 中的兼容模式下打开（请参阅 [_sopen](../../c-runtime-library/reference/sopen-wsopen.md)）。  
  
 在设置这些权限之前，`_creat` 会将当前文件权限掩码应用到 `pmode`（请参阅 [_umask](../../c-runtime-library/reference/umask.md)）。 `_creat` 主要用于与以前的库的兼容性。 在 `oflag` 参数中使用 `_O_CREAT` 和 `_O_TRUNC` 对 `_open` 进行的调用等同于 `_creat` 并且是新代码的优先选择。  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|可选标头|  
|-------------|---------------------|---------------------|  
|`_creat`|\<io.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|  
|`_wcreat`|\<io.h> 或 \<wchar.h>|\<sys/types.h>、\<sys/stat.h>、\<errno.h>|  
  
 有关兼容性的详细信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_creat.c  
// compile with: /W3  
// This program uses _creat to create  
// the file (or truncate the existing file)  
// named data and open it for writing.  
  
#include <sys/types.h>  
#include <sys/stat.h>  
#include <io.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
int main( void )  
{  
   int fh;  
  
   fh = _creat( "data", _S_IREAD | _S_IWRITE ); // C4996  
   // Note: _creat is deprecated; use _sopen_s instead  
   if( fh == -1 )  
      perror( "Couldn't create data file" );  
   else  
   {  
      printf( "Created data file.\n" );  
      _close( fh );  
   }  
}  
```  
  
```Output  
Created data file.  
```  
  
## <a name="see-also"></a>另请参阅  
 [低级别 I/O](../../c-runtime-library/low-level-i-o.md)   
 [_chmod、_wchmod](../../c-runtime-library/reference/chmod-wchmod.md)   
 [_chsize](../../c-runtime-library/reference/chsize.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)   
 [_sopen、_wsopen](../../c-runtime-library/reference/sopen-wsopen.md)   
 [_umask](../../c-runtime-library/reference/umask.md)
