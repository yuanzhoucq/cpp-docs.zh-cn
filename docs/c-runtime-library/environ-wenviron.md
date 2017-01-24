---
title: "_environ、_wenviron | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "environ"
  - "wenviron"
  - "_wenviron"
  - "_environ"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_environ 函数"
  - "_wenviron 函数"
  - "environ 函数"
  - "过程环境"
  - "wenviron 函数"
ms.assetid: 7e639962-6536-47cd-8095-0cbe44a56e03
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _environ、_wenviron
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`_environ` 变量是指向构成进程环境的多字节字符字符串的指针数组的指针。  此全局变量已被弃用，因为出现了更安全的函数版本 [getenv\_s、\_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md) 和 [\_putenv\_s、\_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)，应使用这两个版本来替换此全局变量。  `_environ` 在 Stdlib.h 中声明。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
extern char **_environ;  
```  
  
## 备注  
 在使用 `main` 函数的程序中，`_environ` 在程序启动过程中根据来自操作系统环境的设置进行初始化。  环境包含窗体的一个或多个条目  
  
 `ENVVARNAME` `=string`  
  
 `getenv_s` 和 `putenv_s` 使用 `_environ` 变量来访问和修改环境表。  当调用 `_putenv` 以添加或删除环境设置时，该环境表的大小发生更改。  其在内存中的位置也可能更改，具体取决于程序的内存要求。  `_environ` 的值会自动进行相应调整。  
  
 `_wenviron` 变量在 Stdlib.h 中声明为：  
  
```  
extern wchar_t **_wenviron;  
```  
  
 是 `_environ` 的宽字符版本。  在使用 `wmain` 函数的程序中，`_wenviron` 在程序启动过程中根据来自操作系统环境的设置进行初始化。  
  
 在使用 `main` 的程序中，`_wenviron` 最初为 `NULL`，因为环境是由多字节字符字符串组成的。  在首次调用 `_wgetenv` 或 `_wputenv` 时，会由 `_wenviron` 创建并指向对应的宽字符字符串环境。  
  
 同样，在使用 `wmain` 的程序中，`_environ` 最初是 `NULL`，因为环境是由宽字符字符串组成的。  在首次调用 `_getenv` 或 `_putenv` 时，会由 `_environ` 创建并指向对应的多字节字符字符串环境。  
  
 当程序中同时存在环境的两个副本（MBCS 和 Unicode）时，运行时系统必须保留这两个副本，而这将减慢执行时间。  例如，当调用 `_putenv` 时，也会自动调用 `_wputenv`，以便两个环境字符串相对应。  
  
> [!CAUTION]
>  在极少数情况下，当运行时系统同时保留环境的 Unicode 版本和多字节版本时，两个环境版本可能不完全对应。  这是因为，虽然任何唯一的多字节字符字符串将映射到唯一的 Unicode 字符串，但从唯一的 Unicode 字符串到多字节字符字符串的映射却不一定是唯一的。  因此，两个不同的 Unicode 字符串可能会映射到同一个多字节字符串。  
  
 当使用 [\/MD](../build/reference/md-mt-ld-use-run-time-library.md) 或 `/MDd` 链接时，轮询 Unicode 上下文中的 `_environ` 没有任何意义。  对于 CRT DLL，该程序的类型（宽字节或多字节）是未知的。  因为这是最可能的方案，所以仅创建多字节类型。  
  
 下面的伪代码说明了这一点。  
  
```  
int i, j;  
i = _wputenv( "env_var_x=string1" );  // results in the implicit call:  
                                      // putenv ("env_var_z=string1")  
j = _wputenv( "env_var_y=string2" );  // also results in implicit call:  
                                      // putenv("env_var_z=string2")  
```  
  
 在用于此示例的表示法中，字符字符串不是 C 字符串文本；相反，它们是表示 `_wputenv` 调用中的 Unicode 环境字符串文本和 `putenv` 调用中多字节环境字符串的占位符。  两个不同的 Unicode 环境字符串中的字符占位符“`x`”和“`y`”不会唯一映射到当前 MBCS 中的字符。  相反，这两个占位符都会映射到某些 MBCS 字符“`z`”，这是尝试转换字符串的默认结果。  
  
 因此，在多字节环境中，当“`env_var_z`”的值设置为“`string2`”时，第一次隐式调用 `putenv` 之后“`env_var_z`”的值将为“`string1`”，但此值将在第二次隐式调用 `putenv` 时改写。  因此，Unicode 环境（在 `_wenviron` 中）与多字节环境（在 `_environ` 中）将区分以下这一系列的调用。  
  
## 请参阅  
 [全局变量](../c-runtime-library/global-variables.md)   
 [getenv、\_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)   
 [getenv\_s、\_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)   
 [\_putenv、\_wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [\_putenv\_s、\_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)