---
title: "_get_osfhandle | Microsoft 文档"
ms.custom: 
ms.date: 12/12/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- _get_osfhandle
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
- get_osfhandle
- _get_osfhandle
dev_langs:
- C++
helpviewer_keywords:
- operating systems, getting file handles
- get_osfhandle function
- _get_osfhandle function
- file handles [C++], operating system
ms.assetid: 0bdd728a-4fd8-410b-8c9f-01a121135196
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 4ffc65e12c4a9023d0ef649bbf2cb5e8f7e76808
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="getosfhandle"></a>_get_osfhandle

检索与指定的文件说明符关联的操作系统文件句柄。  
  
## <a name="syntax"></a>语法  
  
```  
intptr_t _get_osfhandle(   
   int fd   
);  
```  
  
### <a name="parameters"></a>参数

*fd*  
现有文件说明符。  
  
## <a name="return-value"></a>返回值

如果返回操作系统文件句柄*fd*有效。 否则，将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则此函数将返回`INVALID_HANDLE_VALUE`(-1)，并将设置`errno`到`EBADF`，指示无效文件句柄。  
  
## <a name="remarks"></a>备注

若要关闭一个通过获取其操作系统 (OS) 的文件句柄的文件`_get_osfhandle`，调用[\_关闭](../../c-runtime-library/reference/close.md)上的文件描述符*fd*。 不要调用`CloseHandle`此函数在返回值上。 基础的操作系统文件句柄拥有的*fd*文件描述符，并关闭时`_close`上调用*fd*。 如果由所拥有的文件描述符`FILE *`流，然后调用[fclose](../../c-runtime-library/reference/fclose-fcloseall.md)上`FILE *`流关闭的文件描述符并基础的操作系统文件句柄。 在这种情况下，不要调用`_close`上的文件描述符。
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_get_osfhandle`|\<io.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅

[文件处理](../../c-runtime-library/file-handling.md)   
[_close](../../c-runtime-library/reference/close.md)   
[_creat、_wcreat](../../c-runtime-library/reference/creat-wcreat.md)   
[_dup、_dup2](../../c-runtime-library/reference/dup-dup2.md)   
[_open、_wopen](../../c-runtime-library/reference/open-wopen.md)
