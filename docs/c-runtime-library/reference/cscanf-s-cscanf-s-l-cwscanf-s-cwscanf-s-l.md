---
title: "_cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_cwscanf_s_l"
  - "_cwscanf_s"
  - "_cscanf_s"
  - "_cscanf_s_l"
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
  - "cscanf_s"
  - "cscanf_s_l"
  - "cwscanf_s"
  - "_cwscanf_s"
  - "_tcscanf_s"
  - "_cscanf_s"
  - "_cwscanf_s_l"
  - "_cscanf_s_l"
  - "cwscanf_s_l"
  - "_tcscanf_s_l"
  - "tcscanf_s"
  - "tcscanf_s_l"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_cscanf_s 函数"
  - "_cscanf_s_l 函数"
  - "_cwscanf_s 函数"
  - "_cwscanf_s_l 函数"
  - "_tcscanf_s 函数"
  - "_tcscanf_s_l 函数"
  - "控制台 [C++], 读取自"
  - "cscanf_s 函数"
  - "cscanf_s_l 函数"
  - "cwscanf_s 函数"
  - "cwscanf_s_l 函数"
  - "数据 [C++], 从控制台读取"
  - "读取数据 [C++], 从控制台中"
  - "tcscanf_s 函数"
  - "tcscanf_s_l 函数"
ms.assetid: 9ccab74d-916f-42a6-93d8-920525efdf4b
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _cscanf_s、_cscanf_s_l、_cwscanf_s、_cwscanf_s_l
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从控制台读取格式数据。  [\_cscanf、\_cscanf\_l、\_cwscanf、\_cwscanf\_l](../../c-runtime-library/reference/cscanf-cscanf-l-cwscanf-cwscanf-l.md) 的这些版本如 [CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _cscanf_s(   
   const char *format [,  
   argument] ...   
);  
int _cscanf_s_l(   
   const char *format,  
   locale_t locale [,  
   argument] ...   
);  
int _cwscanf_s(   
   const wchar_t *format [,  
   argument] ...   
);  
int _cwscanf_s_l(   
   const wchar_t *format,  
   locale_t locale [,  
   argument] ...   
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
 成功转换并分配字段数。  返回值不包括读取，但未赋值的字段。  返回值是`EOF` ，它尝试在文件末尾读取。  当键入被重定向的操作系统命令行级别时，该情况可能发生。  返回值为 0 表示未分配字段。  
  
 这些函数验证其参数。  如果 `format` 是 null 指针，则会调用无效参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许执行继续，则这些函数返回 `EOF`并将 `errno` 设置为`EINVAL`。  
  
## 备注  
 `_cscanf_s` 函数直接从控制台读取数据到由`argument`给定的位置。  [\_getche](../../c-runtime-library/reference/getch-getwch.md) 函数用于读取字符。  每个任意参数必须是指向类型变量的指针，此类型需与 `format` 中的类型说明符对应。  这种格式控制输入字段的解释，并且形式和函数都与 [scanf\_s](../../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 函数的`format` 参数相同。  `_cscanf_s` 正常回显输入字符，如果最后是对 `_ungetch`的调用，则不这样。  
  
 在`scanf` 系列中类似于函数的其他安全版本， 对于类型字段字符`c`、`C`、`s`、`S`和 `[`，`_cscanf_s` 和 `_cswscanf_s` 需要范围参数。  有关详细信息，请参阅[scanf 宽度规范](../../c-runtime-library/scanf-width-specification.md)。  
  
> [!NOTE]
>  大小参数的类型为 `unsigned` 而非 `size_t`。  
  
 这些带有 `_l` 后缀的函数的版本相同，只不过它们使用传递的区域设置参数而不是当前线程区域设置。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tcscanf_s`|`_cscanf_s`|`_cscanf_s`|`_cwscanf_s`|  
|`_tcscanf_s_l`|`_cscanf_s_l`|`_cscanf_s_l`|`_cwscanf_s_l`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_cscanf_s`,`_cscanf_s_l`|\<conio.h\>|  
|`_cwscanf_s`, `_cwscanf_s_l`|\<conio.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_cscanf_s.c  
// compile with: /c  
/* This program prompts for a string  
 * and uses _cscanf_s to read in the response.  
 * Then _cscanf_s returns the number of items  
 * matched, and the program displays that number.  
 */  
  
#include <stdio.h>  
#include <conio.h>  
  
int main( void )  
{  
   int result, n[3];  
   int i;  
  
   result = _cscanf_s( "%i %i %i", &n[0], &n[1], &n[2] );  
   _cprintf_s( "\r\nYou entered " );  
   for( i=0; i<result; i++ )  
      _cprintf_s( "%i ", n[i] );  
   _cprintf_s( "\r\n" );  
}  
```  
  
## 输入  
  
```  
1 2 3  
```  
  
## Output  
  
```  
You entered 1 2 3  
```  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [fscanf\_s、\_fscanf\_s\_l、fwscanf\_s、\_fwscanf\_s\_l](../../c-runtime-library/reference/fscanf-s-fscanf-s-l-fwscanf-s-fwscanf-s-l.md)   
 [scanf\_s、\_scanf\_s\_l、wscanf\_s、\_wscanf\_s\_l](../../c-runtime-library/reference/scanf-s-scanf-s-l-wscanf-s-wscanf-s-l.md)   
 [sscanf\_s、\_sscanf\_s\_l、swscanf\_s、\_swscanf\_s\_l](../../c-runtime-library/reference/sscanf-s-sscanf-s-l-swscanf-s-swscanf-s-l.md)