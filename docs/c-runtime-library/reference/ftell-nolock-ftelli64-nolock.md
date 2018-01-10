---
title: "_ftell_nolock、_ftelli64_nolock | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ftelli64_nolock
- _ftell_nolock
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
- _ftelli64_nolock
- ftelli64_nolock
- ftell_nolock
- _ftell_nolock
dev_langs: C++
helpviewer_keywords:
- ftelli64_nolock function
- _ftelli64_nolock function
- _ftell_nolock function
- ftell_nolock function
- file pointers [C++], getting current position
ms.assetid: 84e68b0a-32f8-4c4a-90ad-3f2387685ede
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 24d5ad81bb19f5a33eb70f6dc40ef41cc5d761d3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ftellnolock-ftelli64nolock"></a>_ftell_nolock、_ftelli64_nolock
获取文件指针的当前位置，而无需锁定线程。  
  
## <a name="syntax"></a>语法  
  
```  
long _ftell_nolock(   
   FILE *stream   
);  
__int64 _ftelli64_nolock(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 以 `FILE` 结构为目标。  
  
## <a name="return-value"></a>返回值  
 与 `ftell` 和 `_ftelli64` 相同。 有关详细信息，请参阅 [ftell、_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)**。**  
  
## <a name="remarks"></a>备注  
 这些函数分别为 `ftell` 和 `_ftelli64` 的非锁定版本。 它们是相同`ftell`和`_ftelli64`，只不过它们不受干扰其他线程。 这些函数可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|可选标头|  
|--------------|---------------------|---------------------|  
|`ftell_nolock`|\<stdio.h>|\<errno.h>|  
|`_ftelli64_nolock`|\<stdio.h>|\<errno.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fgetpos](../../c-runtime-library/reference/fgetpos.md)   
 [fseek、_fseeki64](../../c-runtime-library/reference/fseek-fseeki64.md)   
 [_lseek、_lseeki64](../../c-runtime-library/reference/lseek-lseeki64.md)   
 [ftell、_ftelli64](../../c-runtime-library/reference/ftell-ftelli64.md)