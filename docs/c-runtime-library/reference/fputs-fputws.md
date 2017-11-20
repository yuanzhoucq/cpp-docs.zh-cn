---
title: "fputs、fputws | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fputs
- fputws
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
- fputs
- fputws
- _fputts
dev_langs: C++
helpviewer_keywords:
- streams, writing strings to
- fputws function
- _fputts function
- fputs function
- fputts function
ms.assetid: d48c82b8-aa17-4830-8c7d-30442ddbb326
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 5d3d9a9225a3b6bc0dafd8804f62c61a94acb43c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="fputs-fputws"></a>fputs、fputws
将字符串写入流。  
  
## <a name="syntax"></a>语法  
  
```  
int fputs(   
   const char *str,  
   FILE *stream   
);  
int fputws(   
   const wchar_t *str,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 输出字符串。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 如果成功，其中每个函数都将返回一个非负值。 发生错误时，`fputs` 和 `fputws` 将返回 `EOF`。 如果 `str` 或 `stream` 为 null 指针，则这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些功能将 `errno` 设置为 `EINVAL`，然后 `fputs` 返回 `EOF`，`fputws` 返回 `WEOF`。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 其中每个函数将 `str` 复制到当前位置的输出 `stream`。 `fputws` 将根据 `stream` 是以文本模式还是二进制模式打开的来将宽字符自变量 `str` 作为多字节字符串或宽字符串复制到 `stream`。 函数不会复制终止的 null 字符。  
  
 如果在 ANSI 模式下打开流，则这两个函数行为相同。 `fputs` 当前不支持到 UNICODE 流中的输出。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fputts`|`fputs`|`fputs`|`fputws`|  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fputs`|\<stdio.h>|  
|`fputws`|\<stdio.h> 或 \<wchar.h>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。 与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用中使用它们。 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_fputs.c  
// This program uses fputs to write  
// a single line to the stdout stream.  
  
#include <stdio.h>  
  
int main( void )  
{  
   fputs( "Hello world from fputs.\n", stdout );  
}  
```  
  
```Output  
Hello world from fputs.  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [gets、_getws](../../c-runtime-library/gets-getws.md)   
 [puts、_putws](../../c-runtime-library/reference/puts-putws.md)