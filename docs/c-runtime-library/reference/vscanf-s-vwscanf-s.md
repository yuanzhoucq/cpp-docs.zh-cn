---
title: "vscanf_s、vwscanf_s | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "vscanf_s"
  - "vwscanf_s"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_vtscanf_s"
  - "vscanf_s"
  - "vwscanf_s"
dev_langs: 
  - "C++"
ms.assetid: 23a1c383-5b01-4887-93ce-534a1e38ed93
caps.latest.revision: 6
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# vscanf_s、vwscanf_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从标准输入流中读取格式化数据。  [vscanf、vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
## 语法  
  
```  
int vscanf_s(  
   const char *format,  
   va_list arglist  
);   
int vwscanf_s(  
   const wchar_t *format,  
   va_list arglist  
);  
```  
  
#### 参数  
 `format`  
 窗体控件字符串。  
  
 `arglist`  
 变量参数列表。  
  
## 返回值  
 返回成功转换和赋值的字段数；返回值不包括读取，但未赋值的字段。  返回值为 0 表示未分配字段。  如果出现错误，或者，如果在第一次尝试读取字符时遇到文件结尾字符或字符串结尾字符，则返回值是 `EOF`。  如果 `format` 是一个 `NULL` 指针，无效参数处理程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，`vscanf_s` 和 `vwscanf_s` 返回 `EOF` 并设置 `errno` 为 `EINVAL`。  
  
 有关这些属性和其他错误代码的更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `vscanf_s` 函数将标准输入流 `stdin` 中的数据读取并写入到由 `arglist` 参数列表给定的位置中。  列表中的每个参数必须是指向类型变量的指针，此类型需与 `format` 中的类型说明符对应。  如果复制出现在重叠的字符串之间，则该行为不确定。  
  
 `vwscanf_s` 是 `vscanf_s` 的宽字符版本；`vwscanf_s` 的 `format` 参数是宽字符字符串。  如果流在 ANSI 模式中打开，`vwscanf_s` 和 `vscanf_s` 会具有相同的行为。  `vscanf_s` 不支持 UNICODE 流的输入。  
  
 不同于 `vscanf` 和 `vwscanf`，`vscanf_s` 和 `vwscanf_s` 需要为类型 `c`、`C`、`s`、`S` 的输入参数或封闭在 `[]` 中的字符串控件集指定缓冲区域大小。  字符中的缓冲区区域大小将紧跟指针作为其他参数传递给缓冲区或变量。  `wchar_t` 字符串的字符中的缓冲区区域大小与字节中的大小不同。  
  
 缓冲区大小区域包括终止 null。  您可以使用宽度规范字段以确保读取的标记将放入缓冲区。  如果未使用宽度规范字段，而标记读入又太大以致无法容纳在缓冲区中，则该缓冲区将不写入任何内容。  
  
> [!NOTE]
>  大小参数的类型为 `unsigned` 而非 `size_t`。  
  
 有关详细信息，请参阅 [scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_vtscanf_s`|`vscanf_s`|`vscanf_s`|`vwscanf_s`|  
  
 有关详细信息，请参阅 [格式规范字段：scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`vscanf_s`|\<stdio.h\>|  
|`wscanf_s`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关其他兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_vscanf_s.c  
// compile with: /W3  
// This program uses the vscanf_s and vwscanf_s functions  
// to read formatted input.  
  
#include <stdio.h>  
#include <stdarg.h>  
#include <stdlib.h>  
  
int call_vscanf_s(char *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int call_vwscanf_s(wchar_t *format, ...)  
{  
    int result;  
    va_list arglist;  
    va_start(arglist, format);  
    result = vwscanf_s(format, arglist);  
    va_end(arglist);  
    return result;  
}  
  
int main( void )  
{  
    int   i, result;  
    float fp;  
    char  c, s[81];  
    wchar_t wc, ws[81];  
    result = call_vscanf_s("%d %f %c %C %s %S", &i, &fp, &c, 1,  
                           &wc, 1, s, _countof(s), ws, _countof(ws) );  
    printf( "The number of fields input is %d\n", result );  
    printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);  
    result = call_vwscanf_s(L"%d %f %hc %lc %S %ls", &i, &fp, &c, 2,  
                            &wc, 1, s, _countof(s), ws, _countof(ws) );  
    wprintf( L"The number of fields input is %d\n", result );  
    wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);  
}  
  
```  
  
 如果向此程序提供示例中的输入，则会生成以下输出：  
  
 `71 98.6 h z Byte characters`  
  
 `36 92.3 y n Wide characters`  
  
  **字段输入数是 6**  
**内容为：71 98.599998 h z 字节字符**  
**字段输入数是 6**  
**内容为：36 92.300003 y n 宽字符**   
## .NET Framework 等效项  
  
-   [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
-   [System::Console::ReadLine](https://msdn.microsoft.com/en-us/library/system.console.readline.aspx)  
  
-   也可参见 `Parse` 方法，如 [System::Double::Parse](https://msdn.microsoft.com/en-us/library/system.double.parse.aspx)。  
  
## 请参阅  
 [浮点支持](../../c-runtime-library/floating-point-support.md)   
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [区域设置](../../c-runtime-library/locale.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [scanf、\_scanf\_l、wscanf、\_wscanf\_l](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [vscanf、vwscanf](../../c-runtime-library/reference/vscanf-vwscanf.md)