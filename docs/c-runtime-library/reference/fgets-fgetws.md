---
title: "fgets、fgetws | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- fgets
- fgetws
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
- _fgetts
- fgetws
- fgets
dev_langs: C++
helpviewer_keywords:
- _fgetts function
- streams, getting strings from
- streams, reading from
- fgets function
- fgetws function
- fgetts function
ms.assetid: ad549bb5-df98-4ccd-a53f-95114e60c4fc
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 70cccdc8dea6abb032fbf6170ca84ad866ddd491
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="fgets-fgetws"></a>fgets、fgetws
从流获取字符串。  
  
## <a name="syntax"></a>语法  
  
```  
char *fgets(   
   char *str,  
   int n,  
   FILE *stream   
);  
wchar_t *fgetws(   
   wchar_t *str,  
   int n,  
   FILE *stream   
);  
```  
  
#### <a name="parameters"></a>参数  
 `str`  
 数据的存储位置。  
  
 `n`  
 要读取的最大字符数。  
  
 `stream`  
 指向 `FILE` 结构的指针。  
  
## <a name="return-value"></a>返回值  
 其中每个函数都会返回 `str`。 将返回 `NULL` 指示错误或文件尾条件。 使用 `feof` 或 `ferror` 确定是否出错。 如果 `str` 或 `stream` 是 null 指针，或者 `n` 小于或等于零，则此函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许继续执行，则将 `errno` 设置为 `EINVAL` 并且该函数将返回 `NULL`。  
  
 有关这些代码以及其他错误代码的详细信息，请参阅 [_doserrno、errno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>备注  
 `fgets` 函数将读取输入 `stream` 参数中的一个字符串，并将其存储到 `str` 中。 `fgets`从当前流位置与包括第一个换行符，读取字符数据到末尾流，或直到读取的字符数等于`n`-1，不管先满足。 将向存储在 `str` 中的结果追加一个 null 字符。 换行符（如果读取）将包括在字符串中。  
  
 `fgetws` 是 `fgets` 的宽字符版本。  
  
 `fgetws` 将根据 `str` 是以文本模式还是二进制模式打开的来将宽字符参数 `stream` 作为多字节字符串或宽字符串读取。 有关在 Unicode 和多字节流 I/O 中使用文本和二进制模式的详细信息，请参阅[文本和二进制模式文件 I/O](../../c-runtime-library/text-and-binary-mode-file-i-o.md) 和[文本和二进制模式下的 Unicode 流 I/O](../../c-runtime-library/unicode-stream-i-o-in-text-and-binary-modes.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_fgetts`|`fgets`|`fgets`|`fgetws`|  
  
## <a name="requirements"></a>惠?  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`fgets`|\<stdio.h>|  
|`fgetws`|\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参见“简介”中的 [兼容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="example"></a>示例  
  
```  
// crt_fgets.c  
// This program uses fgets to display  
// a line from a file on the screen.  
//  
  
#include <stdio.h>  
  
int main( void )  
{  
   FILE *stream;  
   char line[100];  
  
   if( fopen_s( &stream, "crt_fgets.txt", "r" ) == 0 )  
   {  
      if( fgets( line, 100, stream ) == NULL)  
         printf( "fgets error\n" );  
      else  
         printf( "%s", line);  
      fclose( stream );  
   }  
}  
```  
  
## <a name="input-crtfgetstxt"></a>输入：crt_fgets.txt  
  
```  
Line one.  
Line two.  
```  
  
### <a name="output"></a>输出  
  
```  
Line one.  
```  
  
## <a name="see-also"></a>请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [gets、_getws](../../c-runtime-library/gets-getws.md)   
 [puts、_putws](../../c-runtime-library/reference/puts-putws.md)