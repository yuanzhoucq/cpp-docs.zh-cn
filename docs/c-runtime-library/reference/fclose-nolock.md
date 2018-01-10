---
title: "_fclose_nolock | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _fclose_nolock
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
- fclose_nolock
- _fclose_nolock
dev_langs: C++
helpviewer_keywords:
- streams, closing
- fclose_nolock function
- _fclose_nolock function
ms.assetid: b4af4392-5fc8-49bb-9fe2-ca7293d3ce04
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a993376f1174a86506f5c61d3b403953bedec3f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fclosenolock"></a>_fclose_nolock
在不锁定线程的情况下关闭流。  
  
## <a name="syntax"></a>语法  
  
```  
int _fclose_nolock(   
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果已成功关闭流，则 `fclose` 返回 0。 返回 `EOF` 以指示错误。  
  
## <a name="remarks"></a>备注  
 此函数为 `fclose` 的非锁定版本。 它完全相同，只不过它可能受到其他线程的影响。 它可能更快，因为它不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用此函数，如单线程应用程序或调用范围已处理线程隔离的区域。  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`_fclose_nolock`|\<stdio.h>|  
  
 有关更多兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_close](../../c-runtime-library/reference/close.md)   
 [_fdopen、_wfdopen](../../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fflush](../../c-runtime-library/reference/fflush.md)   
 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen、_wfreopen](../../c-runtime-library/reference/freopen-wfreopen.md)