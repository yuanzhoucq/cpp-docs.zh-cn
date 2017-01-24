---
title: "gets_s、_getws_s | Microsoft Docs"
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
  - "_getws_s"
  - "gets_s"
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
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_getws_s"
  - "gets_s"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_getws_s 函数"
  - "缓冲区溢出"
  - "缓冲区, 避免溢出"
  - "缓冲区, 缓冲区溢出"
  - "gets_s 函数"
  - "getws_s 函数"
  - "文本行, 获取"
  - "标准输入, 读取自"
  - "流, 获取行"
ms.assetid: 5880c36f-122c-4061-a1a5-aeeced6fe58c
caps.latest.revision: 29
caps.handback.revision: 27
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# gets_s、_getws_s
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

从 `stdin` 流获取线。  [](../../c-runtime-library/gets-getws.md "gets, _getws")[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) 所述，其安全得到了增强。  
  
## 语法  
  
```  
char *gets_s(   
   char *buffer,  
   size_t sizeInCharacters  
);  
wchar_t *_getws_s(   
   wchar_t *buffer,  
   size_t sizeInCharacters  
);  
template <size_t size>  
char *gets_s(   
   char (&buffer)[size]  
); // C++ only  
template <size_t size>  
wchar_t *_getws_s(   
   wchar_t (&buffer)[size]  
); // C++ only  
```  
  
#### 参数  
 \[out\] `buffer`  
 输入字符串的存储位置。  
  
 \[in\] `sizeInCharacters`  
 缓冲区的大小。  
  
## 返回值  
 如果成功，则返回 `buffer`。  `NULL` 指针表示错误或文件结尾条件。  使用 [ferror](../../c-runtime-library/reference/ferror.md) 或 [feof](../../c-runtime-library/reference/feof.md) 确定哪个已发生。  
  
## 备注  
 The `gets_s` 函数从标准输入流 `stdin` 中读取一行并保存在 `buffer`中.  行包含所有字符，也包括第一个换行符 \(“\\n”\)。  在返回行之前`gets_s` 使用 null 字符 \(“\\0 ”\)替换换行符。  相反，`fgets_s` 功能保留换行符。  
  
 如果第一个字符是读取文件结尾字符，null 字符在 `buffer` 开头就被储存且返回 `NULL` 。  
  
 `_wsetlocale_getws`  是 `gets_s`  的宽字符版本；其声明和返回值都是宽字符字符串。  
  
 如果 `buffer` 是 `NULL` 或 `sizeInCharacters` 小于或等于零，或者如果缓冲区因过小而无法包含一行输入和 null 结束符，这些函数调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果允许执行继续，则这些函数返回 `NULL` 并设置为 `ERANGE` 。  
  
 在 C\+\+ 中，使用这些函数由模板重载简化；重载可以自动推导出缓冲区长度 \(不再需要指定大小参数\)，并且它们可以自动用以更新、更安全的对应物替换旧的、不安全的函数。  有关详细信息，请参阅[安全模板重载](../../c-runtime-library/secure-template-overloads.md)。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_getts`|`gets_s`|`gets_s`|`_getws`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`gets_s`|\<stdio.h\>|  
|`_getws`|\<stdio.h\> 或 \<wchar.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```  
// crt_gets_s.c  
// This program retrieves a string from the stdin and   
// prints the same string to the console.  
  
#include <stdio.h>  
  
int main( void )  
{  
   char line[21]; // room for 20 chars + '\0'  
   gets_s( line, 20 );  
   printf( "The line entered was: %s\n", line );  
}  
```  
  
  **`Hello there!`输入的行为: Hello there\!**   
## .NET Framework 等效项  
 [System::Console::Read](https://msdn.microsoft.com/en-us/library/system.console.read.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [gets、\_getws](../../c-runtime-library/gets-getws.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [puts、\_putws](../../c-runtime-library/reference/puts-putws.md)