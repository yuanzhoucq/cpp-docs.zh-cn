---
title: "scanf、_scanf_l、wscanf、_wscanf_l | Microsoft Docs"
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
  - "_wscanf_l"
  - "scanf"
  - "_scanf_l"
  - "wscanf"
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
  - "_tscanf"
  - "_scanf_l"
  - "wscanf"
  - "_wscanf_l"
  - "scanf"
  - "_tscanf_l"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_scanf_l 函数"
  - "_tscanf 函数"
  - "_tscanf_l 函数"
  - "_wscanf_l 函数"
  - "数据 [C++], 从输入流中读取"
  - "格式化的数据 [C++], 从输入流"
  - "读取数据 [C++], 从输入流"
  - "scanf 函数"
  - "scanf_l 函数"
  - "tscanf 函数"
  - "tscanf_l 函数"
  - "wscanf 函数"
  - "wscanf_l 函数"
ms.assetid: 73eac607-117f-4be4-9ff0-4afd9cf3c848
caps.latest.revision: 25
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# scanf、_scanf_l、wscanf、_wscanf_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从标准输入流中读取格式化数据。  有关这些函数的更多安全版本，请参见 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)。  
  
## 语法  
  
```  
int scanf(  
   const char *format [,  
   argument]...   
);  
int _scanf_l(  
   const char *format,  
   locale_t locale [,  
   argument]...   
);  
int wscanf(  
   const wchar_t *format [,  
   argument]...   
);  
int _wscanf_l(  
   const wchar_t *format,  
   locale_t locale [,  
   argument]...   
);  
```  
  
#### 参数  
 `format`  
 窗体控件字符串。  
  
 `argument`  
 可选参数。  
  
 `locale`  
 要使用的区域设置。  
  
## 返回值  
 返回成功转换和赋值的字段数；返回值不包括读取，但未赋值的字段。  返回值为 0 表示未分配字段。  
  
 如果 `format` 是一个 `NULL` 指针，无效参数处理程序将按 [参数验证](../../c-runtime-library/parameter-validation.md) 中所述进行调用。  如果允许执行继续，则这些函数返回 `EOF` 并将 `errno` 设置为 `EINVAL`。  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `scanf` 函数从标准输入流 `stdin` 读取数据并将数据写入由 `argument` 给定的位置中。   `argument` 列表中的每个参数必须是指向类型变量的指针，此类型需与`format`中的类型说明符对应。  如果复制出现在重叠的字符串之间，则该行为不确定。  
  
> [!IMPORTANT]
>  用 `scanf` 读取字符串时，始终指定 `%s` 格式的宽度（例如，`"%32s"` 而非 `"%s"`）；否则，不适当的格式输入可能会导致缓冲区溢出。  或者，考虑使用 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md) 或 [fgets](../../c-runtime-library/reference/fgets-fgetws.md)。  
  
 `wscanf` 是 `scanf` 的宽字符版本；`wscanf` 的 `format` 参数是宽字符字符串。  如果流在 ANSI 模式中打开，`wscanf` 和 `scanf` 会具有相同的行为。  `scanf` 当前不支持 UNICODE 流的输入。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tscanf`|`scanf`|`scanf`|`wscanf`|  
|`_tscanf_l`|`_scanf_l`|`_scanf_l`|`_wscanf_l`|  
  
 有关详细信息，请参阅 [格式规范字段— scanf 和 wscanf 函数](../../c-runtime-library/format-specification-fields-scanf-and-wscanf-functions.md)。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`scanf`, `_scanf_l`|\<stdio.h\>|  
|`wscanf`, `_wscanf_l`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_scanf.c  
// compile with: /W3  
 /* This program uses the scanf and wscanf functions  
  * to read formatted input.  
  */  
  
#include <stdio.h>  
  
int main( void )  
{  
   int   i, result;  
   float fp;  
   char  c, s[81];  
   wchar_t wc, ws[81];  
   result = scanf( "%d %f %c %C %80s %80S", &i, &fp, &c, &wc, s, ws ); // C4996  
   // Note: scanf and wscanf are deprecated; consider using scanf_s and wscanf_s  
   printf( "The number of fields input is %d\n", result );  
   printf( "The contents are: %d %f %c %C %s %S\n", i, fp, c, wc, s, ws);  
   result = wscanf( L"%d %f %hc %lc %80S %80ls", &i, &fp, &c, &wc, s, ws ); // C4996  
   wprintf( L"The number of fields input is %d\n", result );  
   wprintf( L"The contents are: %d %f %C %c %hs %s\n", i, fp, c, wc, s, ws);  
}  
```  
  
  **`71 98.6 h z 字节字符 36 92.3 y n 宽字符`输入的字段数为 6**  
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
 [fscanf、\_fscanf\_l、fwscanf、\_fwscanf\_l](../../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)   
 [printf、\_printf\_l、wprintf、\_wprintf\_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [sprintf、\_sprintf\_l、swprintf、\_swprintf\_l、\_\_swprintf\_l](../../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)   
 [sscanf、\_sscanf\_l、swscanf、\_swscanf\_l](../../c-runtime-library/reference/sscanf-sscanf-l-swscanf-swscanf-l.md)