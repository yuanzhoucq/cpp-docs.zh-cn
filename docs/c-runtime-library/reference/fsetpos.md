---
title: "fsetpos | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: fsetpos
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
f1_keywords: fsetpos
dev_langs: C++
helpviewer_keywords:
- streams, setting position indicators
- fsetpos function
ms.assetid: 6d19ff48-1a2b-47b3-9f23-ed0a47b5a46e
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 504ab55aadc315dcf06c07a999f2a7d3dfca630b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fsetpos"></a>fsetpos
设置流位置指示器。  
  
## <a name="syntax"></a>语法  
  
```  
int fsetpos(   
   FILE *stream,  
   const fpos_t *pos   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `pos`  
 位置指示器存储。  
  
## <a name="return-value"></a>返回值  
 如果成功，则 `fsetpos` 返回 0。 失败时，该函数返回一个非零值，并将 `errno` 设置为下列任一清单常量（在 ERRNO.H 中定义）： `EBADF`，这意味着文件不可访问或 `stream` 指向的对象不是有效的文件结构；或 `EINVAL`，这意味着传递了 `stream` 或 `pos` 的一个无效值。 如果传入了无效参数，这些函数则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  
  
 有关这些代码以及其他返回代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `fsetpos`函数设置的文件位置指示器`stream`为的值`pos`，这在调用中获取`fgetpos`针对`stream`。 该函数清除文件尾指示器和撤消的任何影响[ungetc](../../c-runtime-library/reference/ungetc-ungetwc.md)上`stream`。 在调用 `fsetpos` 后，`stream` 上的下一个操作可能为输入或输出。  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fsetpos`|\<stdio.h>|  
  
 有关其他兼容性信息，请参阅“简介”中的[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
 请参阅 [fgetpos](../../c-runtime-library/reference/fgetpos.md) 的示例。  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)