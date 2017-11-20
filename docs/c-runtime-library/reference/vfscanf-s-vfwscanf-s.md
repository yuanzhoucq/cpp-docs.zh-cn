---
title: "vfscanf_s、vfwscanf_s | Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- vfscanf_s
- vfwscanf_s
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
apitype: DLLExport
f1_keywords:
- vfscanf_s
- vfwscanf_s
- _vftscanf_s
dev_langs: C++
ms.assetid: 9b0133f0-9a18-4581-b24b-3b72683ad432
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 6f6ffb0f0c4ad4e53c19daa226e12517efab315f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="vfscanfs-vfwscanfs"></a>vfscanf_s、vfwscanf_s
从流中读取格式化数据。 这些 vfscanf、vfwscanf 版本具有安全增强功能，如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)所述。  
  
## <a name="syntax"></a>语法  
  
```  
int vfscanf_s(   
   FILE *stream,  
   const char *format,  
   va_list arglist  
);  
int vfwscanf_s(   
   FILE *stream,  
   const wchar_t *format,  
   va_list arglist  
);  
  
```  
  
#### <a name="parameters"></a>参数  
 `stream`  
 指向 `FILE` 结构的指针。  
  
 `format`  
 窗体控件字符串。  
  
 `arglist`  
 变量参数列表。  
  
## <a name="return-value"></a>返回值  
 每个函数都将返回成功转换并分配的字段数；返回值不包括已读取但未分配的字段。 返回值为 0 表示没有分配任何字段。 如果出现错误或在首次转换前达到文件流的结尾，则 `vfscanf_s` 和 `vfwscanf_s` 的返回值为 `EOF`。  
  
 这些函数验证其参数。 如果 `stream` 是无效文件指针，或 `format` 是 null 指针，这些函数将调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。 如果允许执行继续，则这些函数将返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
## <a name="remarks"></a>备注  
 `vfscanf_s` 函数将从 `stream` 的当前位置将数据读取到 `arglist` 参数列表（如果有）提供的位置。 列表中的每个参数都必须为指向类型的变量的指针，该类型与 `format` 中的类型说明符对应。 `format` 控制输入字段的解释，格式和函数与 `scanf_s` 的 `format` 参数相同；有关 `format` 的说明，请参阅[格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。 `vfwscanf_s` 是 `vfscanf_s` 的宽字符版本；`vfwscanf_s` 格式参数是宽字符字符串。 如果在 ANSI 模式下打开流，则这些函数行为相同。 `vfscanf_s` 当前不支持 UNICODE 流的输入。  
  
 更安全的函数（带有 `_s` 后缀）与其他版本之间的主要区别在于，更安全的函数需要每个 `c`、`C`、`s`、`S` 和 `[` 类型字段的以字符为单位的大小作为紧跟变量的参数进行传递。 有关详细信息，请参阅 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 和 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。  
  
> [!NOTE]
>  大小参数的类型具有 `unsigned`，而不具有 `size_t`。  
  
### <a name="generic-text-routine-mappings"></a>一般文本例程映射  
  
|TCHAR.H 例程|未定义 _UNICODE 和 _MBCS|已定义 _MBCS|已定义 _UNICODE|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_vftscanf_s`|`vfscanf_s`|`vfscanf_s`|`vfwscanf_s`|  
  
## <a name="requirements"></a>要求  
  
|函数|必需的标头|  
|--------------|---------------------|  
|`vfscanf_s`|\<stdio.h>|  
|`vfwscanf_s`|\<stdio.h> 或 \<wchar.h>|  
  
 有关其他兼容性信息，请参阅[兼容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="example"></a>示例  
  
```  
// crt_vfscanf_s.c  
// compile with: /W3  
// This program writes formatted  
// data to a file. It then uses vfscanf_s to  
// read the various data back from the file.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
FILE *stream;  
  
int call_vfscanf_s(FILE * istream, char * format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vfscanf_s(istream, format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main(void)  
{  
    long l;  
    float fp;  
    char s[81];  
    char c;  
  
    if (fopen_s(&stream, "vfscanf_s.out", "w+") != 0)  
    {  
        printf("The file vfscanf_s.out was not opened\n");  
    }  
    else  
    {  
        fprintf(stream, "%s %ld %f%c", "a-string",  
            65000, 3.14159, 'x');  
        // Security caution!  
        // Beware loading data from a file without confirming its size,  
        // as it may lead to a buffer overrun situation.  
  
        // Set pointer to beginning of file:  
        fseek(stream, 0L, SEEK_SET);  
  
        // Read data back from file:  
        call_vfscanf_s(stream, "%s %ld %f%c", s, _countof(s), &l, &fp, &c, 1);  
  
        // Output data read:   
        printf("%s\n", s);  
        printf("%ld\n", l);  
        printf("%f\n", fp);  
        printf("%c\n", c);  
  
        fclose(stream);  
    }  
}  
  
```  
  
```Output  
a-string  
65000  
3.141590  
x  
```  
  
## <a name="see-also"></a>另请参阅  
 [流 I/O](../../c-runtime-library/stream-i-o.md)   
 [_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l](../../c-runtime-library/reference/cscanf-s-cscanf-s-l-cwscanf-s-cwscanf-s-l.md)   
 [fprintf_s、_fprintf_s_l、fwprintf_s、_fwprintf_s_l](../../c-runtime-library/reference/fprintf-s-fprintf-s-l-fwprintf-s-fwprintf-s-l.md)   
 [scanf_s、_scanf_s_l、wscanf_s、_wscanf_s_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf_s、_sscanf_s_l、swscanf_s、_swscanf_s_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)   
 [fscanf、_fscanf_l、fwscanf、_fwscanf_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [vfscanf、vfwscanf](../../c-runtime-library/reference/vfscanf-vfwscanf.md)