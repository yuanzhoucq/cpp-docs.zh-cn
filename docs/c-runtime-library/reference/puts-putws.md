---
title: "puts、_putws | Microsoft Docs"
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
  - "_putws"
  - "puts"
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
  - "_putts"
  - "_putws"
  - "puts"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putts 函数"
  - "_putws 函数"
  - "puts 函数"
  - "putts 函数"
  - "putws 函数"
  - "标准输出, 写入"
  - "字符串 [C++], 写入"
ms.assetid: 32dada12-ed45-40ac-be06-3feeced9ecd6
caps.latest.revision: 15
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# puts、_putws
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

向**stdout**中写入一个字符串。  
  
## 语法  
  
```  
  
      int puts(  
   const char *str   
);  
int _putws(  
   const wchar_t *str   
);  
```  
  
#### 参数  
 `str`  
 输出字符串  
  
## 返回值  
 如果成功返回非负值。  如果 `puts` 失败，则返回；`EOF`如果 `_putws` 失败，则返回 **WEOF**。  如果 `str` 是空指针，则会调用无效参数处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md) 所述。  如果允许继续执行, 函数设置`errno` 为 `EINVAL` 并且返回 `EOF` 或者**WEOF**.  
  
 有关这些属性和其他错误代码的信息，请参见 [\_doserrno、errno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 备注  
 `puts` 函数写入 `str`到标准输出流 **stdout**，替换字符串的终止 null 字符 \(“\\0 "\) 将一个换行符 \(“\\n”\) 在输出流。  
  
 `_putws` 是 `puts`的宽字符版本；如果流在 ANSI 模式下是公开的则两个函数具有相同行为。  `puts` 当前不支持输出到 UNICODE 流。  
  
 在 Windows 2000 和更高版本，**\_putwch** 使用CONSOLE LOCALE设置写入Unicode字符。  
  
### 一般文本例程映射  
  
|TCHAR.H 例程|未定义 \_UNICODE & \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_putts`|`puts`|`puts`|`_putws`|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`puts`|\<stdio.h\>|  
|`_putws`|\<stdio.h\>|  
  
 控制台在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中不受支持。  与控制台 `stdin`、`stdout` 和 `stderr` 关联的标准流句柄必须重定向，然后 C 运行时函数才可以在 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序中使用它们。  有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
  
```  
// crt_puts.c  
/* This program uses puts to write a string to stdout.  
 */  
  
#include <stdio.h>  
  
int main( void )  
{  
   puts( "Hello world from puts!" );  
}  
```  
  
## Output  
  
```  
Hello world from puts!  
```  
  
## .NET Framework 等效项  
 [System::Console::Write](https://msdn.microsoft.com/en-us/library/system.console.write.aspx)  
  
## 请参阅  
 [流 I\/O](../../c-runtime-library/stream-i-o.md)   
 [fputs、fputws](../../c-runtime-library/reference/fputs-fputws.md)   
 [fgets、fgetws](../../c-runtime-library/reference/fgets-fgetws.md)