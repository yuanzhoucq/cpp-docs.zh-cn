---
title: "fclose、_fcloseall | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fclose
- _fcloseall
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
- fclose
- _fcloseall
dev_langs:
- C++
helpviewer_keywords:
- fclose function
- streams, closing
- _fcloseall function
ms.assetid: c3c6ea72-92c6-450a-a33e-3e568d2784a4
caps.latest.revision: 17
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
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 46b9086e4c75a699acec47e3b6b68ba7bcc231cf
ms.contentlocale: zh-cn
ms.lasthandoff: 03/30/2017

---
# <a name="fclose-fcloseall"></a>fclose、_fcloseall
关闭流 (`fclose`) 或关闭所有打开的流 (`_fcloseall`)。  
  
## <a name="syntax"></a>语法  
  
```  
int fclose(   
   FILE *stream   
);  
int _fcloseall( void );  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果已成功关闭流，则 `fclose` 返回 0。 `_fcloseall` 返回已关闭流的总数。 这两个函数都返回 `EOF`，表示出现错误。  
  
## <a name="remarks"></a>备注  
 `fclose` 函数关闭 `stream`。 如果 `stream` 为 `NULL`，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则 `fclose` 将 `errno` 设置为 `EINVAL` 并返回 `EOF`。 建议在调用此函数前始终检查 `stream` 指针。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
 `_fcloseall`函数将关闭所有打开的流，`stdin`、`stdout`、`stderr`（以及在 MS-DOS 中的 `_stdaux` 和 `_stdprn`）除外。 它还将关闭并删除 `tmpfile` 所创建的任何临时文件。 在这两个函数中，与流相关联的所有缓冲区在关闭前都会进行刷新。 系统分配的缓冲区在流关闭时释放。 用户使用 `setbuf` 和 `setvbuf` 分配的缓冲区不会自动释放。  
  
 **注意：**将这些函数用于关闭流时，基础文件描述符和 OS 文件句柄（或套接字）以及流都将被关闭。 因此，如果文件最初作为文件句柄或文件描述符打开并使用 `fclose` 关闭，则不要同时调用 `_close` 来关闭文件描述符；不要调用 Win32 函数 `CloseHandle` 来关闭文件句柄。  
  
 `fclose` 和 `_fcloseall` 包含可抵御来自其他线程干扰的代码。 有关 `fclose` 的非锁定版本，请参阅 `_fclose_nolock`。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fclose`|\<stdio.h>|  
|`_fcloseall`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [fopen](../../c-runtime-library/reference/fopen-wfopen.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_fdopen、_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)
