---
title: "gets、_getws |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getws
- gets
apilocation:
- msvcr80.dll
- msvcr90.dll
- msvcr120.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcrt.dll
- msvcr100.dll
apitype: DLLExport
f1_keywords:
- _getts
- gets
- _getws
dev_langs:
- C++
helpviewer_keywords:
- getws function
- getts function
- _getws function
- lines, getting
- streams, getting lines
- _getts function
- gets function
- standard input, reading from
ms.assetid: 1ec2dd4b-f801-48ea-97c2-892590f16024
caps.latest.revision: 32
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
translationtype: Human Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: dd8739365a4523fe1ecb9aee9931b376edf2b390
ms.lasthandoff: 03/30/2017

---
# <a name="gets-getws"></a>gets、_getws
从 `stdin` 流中获取行。 提供这些函数的更多安全版本；请参阅 [gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)。  
  
> [!IMPORTANT]
>  这些函数已过时。 从 Visual Studio 2015 开始，CRT 中不再提供这些函数。 这些函数（gets_s 和 _getws_s）的安全版本仍然可用。 有关这些备用函数的信息，请参阅 [gets_s、_getws_s](../c-runtime-library/reference/gets-s-getws-s.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。 有关详细信息，请参阅 [/ZW 不支持的 CRT 函数](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>语法  
  
```  
char *gets(   
   char *buffer   
);  
wchar_t *_getws(   
   wchar_t *buffer   
);  
template <size_t size>  
char *gets(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### <a name="parameters"></a>参数  
 `buffer`  
 输入字符串的存储位置。  
  
## <a name="return-value"></a>返回值  
 如果成功，则返回其参数。 `NULL` 指针指示错误或文件尾条件。 使用 [ferror](../c-runtime-library/reference/ferror.md) 或 [feof](../c-runtime-library/reference/feof.md) 确定已发生哪种情况。 如果 `buffer` 为 `NULL`，这些函数会调用无效的参数处理程序，如[参数验证](../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数返回 `NULL` 并将 errno 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `gets` 函数从标准输入流 `stdin` 中读取一个行并将该行存储在 `buffer` 中。 该行由第一个换行符(“\n”)之前的所有字符和该换行符构成。 随后，在返回行之前，`gets` 会将换行符替换为 null 字符（“\0”）。 相反，`fgets` 函数将保留换行符。 `_getws` 是 `gets` 的宽字符版本；其参数和返回值都是宽字符字符串。  
  
> [!IMPORTANT]
>  由于无法限制 gets 读取的字符数，因此不受信任的输入容易导致缓冲区溢出。 请改用 `fgets` 。  
  
 在 C++ 中，这些函数具有模板重载，以调用这些函数的更新、更安全副本。 有关详细信息，请参阅[安全模板重载](../c-runtime-library/secure-template-overloads.md)。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_getts`|`gets`|`gets`|`_getws`|  
  
## <a name="requirements"></a>要求  
  
|例程|必需的标头|  
|-------------|---------------------|  
|`gets`|\<stdio.h>|  
|`_getws`|\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_gets.c  
// compile with: /WX /W3  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets( line );  // C4996  
   // Danger: No way to limit input to 20 chars.  
   // Consider using gets_s instead.  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
 请注意，20 个字符以上的输入将溢出行缓冲区，并且会导致程序发生崩溃。  
  
```Output  
  
Hello there!The line entered was: Hello there!  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../c-runtime-library/stream-i-o.md)   
 [fgets、fgetws](../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs、fputws](../c-runtime-library/reference/fputs-fputws.md)   
 [puts、_putws](../c-runtime-library/reference/puts-putws.md)
