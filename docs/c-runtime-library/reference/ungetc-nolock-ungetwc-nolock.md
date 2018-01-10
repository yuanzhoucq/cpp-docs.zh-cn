---
title: "_ungetc_nolock、_ungetwc_nolock | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _ungetwc_nolock
- _ungetc_nolock
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
- _ungettc_nolock
- ungetwc_nolock
- ungetc_nolock
- _ungetc_nolock
- _ungetwc_nolock
dev_langs: C++
helpviewer_keywords:
- _ungettc_nolock function
- _ungetwc_nolock function
- characters, pushing back onto stream
- _ungetc_nolock function
- ungetwc_nolock function
- ungettc_nolock function
- ungetc_nolock function
ms.assetid: aa02d5c2-1be1-46d2-a8c4-b61269e9d465
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 050e70744ca47b508c65905ecf95b17f42c38b8b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="ungetcnolock-ungetwcnolock"></a>_ungetc_nolock、_ungetwc_nolock
将字符重新推送到流上。  
  
## <a name="syntax"></a>语法  
  
```  
int _ungetc_nolock(  
   int c,  
   FILE *stream   
);  
wint_t _ungetwc_nolock(  
   wint_t c,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `c`  
 要推送的字符。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，其中每个函数将返回字符自变量`c`。 如果无法推送回 `c` 或未读取任何字符，则输入流不改变且 `_ungetc_nolock` 返回 `EOF`；`_ungetwc_nolock` 返回 `WEOF`。 如果 `stream` 为 `NULL`，则将返回 `EOF` 或 `WEOF`，并且 `errno` 将设置为 `EINVAL`。  
  
 有关这些代码及其他错误代码的信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 这些函数是 `ungetc` 和 `ungetwc` 的非锁定版本。 带 `_nolock` 后缀的版本相同，只不过它们可能受到其他线程的影响。 它们可能更快，因为它们不会产生锁定其他线程的开销。 仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_ungettc_nolock`|`_ungetc_nolock`|`_ungetc_nolock`|`_ungetwc_nolock`|  
  
## <a name="requirements"></a>惠?  
  
|例程所返回的值|必需的标头|  
|-------------|---------------------|  
|`_ungetc_nolock`|\<stdio.h>|  
|`_ungetwc_nolock`|\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [getc、getwc](../../c-runtime-library/reference/getc-getwc.md)   
 [putc、putwc](../../c-runtime-library/reference/putc-putwc.md)