---
title: "_putch、_putwch | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putwch"
  - "_putch"
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
  - "api-ms-win-crt-conio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_putch"
  - "putwch"
  - "_putwch"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putch 函数"
  - "_putwch 函数"
  - "字符, 写入"
  - "控制台, 将字符写入到"
  - "putch 函数"
  - "putwch 函数"
ms.assetid: 3babc7cf-e333-405d-8449-c788d61d51aa
caps.latest.revision: 19
caps.handback.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putch、_putwch
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

将字符写入控制台。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
      int _putch(  
int c   
);  
wint_t _putwch(  
   wchar_t c  
);  
```  
  
#### 参数  
 `c`  
 要输出的字符。  
  
## 返回值  
 如果成功，则返回 `c`。  如果 `_putch` 失败，则返回`EOF`；如果 **\_putwch** 失败，则返回 **WEOF**。  
  
## 备注  
 这些功能对控制台直接写入字符 `c`，不缓冲。  在 windows NT，**\_putwch** 编写使用当前控件台区域设置的 Unicode 字符。  
  
 有**\_nolock** 后缀的版本是相同的，但它们不能阻止其他线程的干扰。  有关更多信息，请参见`_putch_nolock`、`_putwch_nolock`。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|**\_puttch**|`_putch`|`_putch`|**\_putwch**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_putch`|\<conio.h\>|  
|**\_putwch**|\<conio.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 示例  
 请参见[\_getch](../../c-runtime-library/reference/getch-getwch.md)示例。  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)