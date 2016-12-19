---
title: "_putch_nolock、_putwch_nolock | Microsoft Docs"
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
  - "_putwch_nolock"
  - "_putch_nolock"
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
  - "_putch_nolock"
  - "_puttch_nolock"
  - "putch_nolock"
  - "putwch_nolock"
  - "_putwch_nolock"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putch_nolock 函数"
  - "_puttch_nolock 函数"
  - "_putwch_nolock 函数"
  - "字符, 写入"
  - "控制台, 将字符写入到"
  - "putch_nolock 函数"
  - "puttch_nolock 函数"
  - "putwch_nolock 函数"
ms.assetid: edbc811d-bac6-47fa-a872-fe4f3a1590b0
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putch_nolock、_putwch_nolock
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

无需锁定线程就可将一个字符写入控制台。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
  
      int _putch_nolock(  
int c   
);  
wint_t _putwch_nolock(  
wchar_t c  
);  
```  
  
#### 参数  
 *c*  
 要输出的字符。  
  
## 返回值  
 如果成功，则返回 *c*。  如果 **\_putch\_nolock** 失败，则返回**EOF**；如果 **\_putwch\_nolock** 失败，则返回 **WEOF**。  
  
## 备注  
 **\_putch\_nolock** 和 **\_putwch\_nolock** 分别与**\_putch** 和 **\_putwch**相同，除了它们受其他线程的干扰。  它们可能更快，因为它们不会产生锁定其他线程的开销。  仅在线程安全的上下文中使用这些函数，如单线程应用程序或调用范围已经处理线程隔离。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|**\_puttch\_nolock**|**\_puttch\_nolock**|**\_puttch\_nolock**|**\_putwch\_nolock**|  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**\_puttch\_nolock**|\<conio.h\>|  
|**\_putwch\_nolock**|\<conio.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 请参阅  
 [控制台和端口 I\/O](../../c-runtime-library/console-and-port-i-o.md)   
 [\_cprintf、\_cprintf\_l、\_cwprintf、\_cwprintf\_l](../../c-runtime-library/reference/cprintf-cprintf-l-cwprintf-cwprintf-l.md)   
 [\_getch、\_getwch](../../c-runtime-library/reference/getch-getwch.md)