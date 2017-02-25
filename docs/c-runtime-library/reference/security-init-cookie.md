---
title: "__security_init_cookie | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__security_init_cookie"
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
  - "security_init_cookie"
  - "__security_init_cookie"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__security_init_cookie 函数"
  - "全局安全 Cookie"
  - "安全 Cookie [C++]"
  - "security_init_cookie 函数"
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# __security_init_cookie
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

初始化全局安全 Cookie。  
  
## 语法  
  
```  
void __security_init_cookie(void);  
```  
  
## 备注  
 全局安全 Cookie 用于在使用 [\/GS（缓冲区安全检查）](../../build/reference/gs-buffer-security-check.md) 编译的代码中和使用异常处理的代码中提供缓冲区溢出保护。  进入受到溢出保护的函数时，Cookie 被置于堆栈之上；退出时，会将堆栈上的值与全局 Cookie 进行比较。  它们之间存在任何差异则表示已经发生缓冲区溢出，并导致该程序的立即终止。  
  
 通常，在初始化时，CRT 会调用 `__security_init_cookie`。  如果绕开 CRT 初始化（例如，使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 指定一个入口点），则必须自己调用 `__security_init_cookie`。  如果不调用 `__security_init_cookie`，全局安全 Cookie 将设定为默认值，缓冲区溢出保护将受到威胁。  由于攻击者可利用此默认 Cookie 值使缓冲区溢出检查无效，我们建议，在定义自己的入口点时，始终调用 `__security_init_cookie`。  
  
 在进入任何受到溢出保护的函数前，必须调用 `__security_init_cookie`，否则将检测到虚假的缓冲区溢出。  有关详细信息，请参阅[C 运行时错误 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)。  
  
## 示例  
 请参阅 [C 运行时错误 R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md) 中的示例。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`__security_init_cookie`|\<process.h\>|  
  
 `__security_init_cookie` 是标准 C 运行库的 Microsoft 扩展。  有关兼容性信息，请参见 [兼容性](../../c-runtime-library/compatibility.md)。  
  
## .NET Framework 等效项  
 不适用。此函数应仅从本机代码（而非托管代码）调用。  
  
## 请参阅  
 [编译器安全检查深入介绍](http://go.microsoft.com/fwlink/?linkid=7260)