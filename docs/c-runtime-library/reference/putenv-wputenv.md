---
title: "_putenv、_wputenv | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_putenv"
  - "_wputenv"
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
  - "api-ms-win-crt-environment-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_tputenv"
  - "_wputenv"
  - "_putenv"
  - "wputenv"
  - "tputenv"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_putenv 函数"
  - "_tputenv 函数"
  - "_wputenv 函数"
  - "环境变量, 创建"
  - "环境变量, 删除"
  - "环境变量, 修改"
  - "putenv 函数"
  - "tputenv 函数"
  - "wputenv 函数"
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _putenv、_wputenv
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

创建，修改或移除环境变量。  有关这些函数的更多安全版本，请参见 [\_putenv\_s、\_wputenv\_s](../../c-runtime-library/reference/putenv-s-wputenv-s.md)。  
  
> [!IMPORTANT]
>  此 API 不能用于在 Windows 运行时中执行的应用程序。  有关详细信息，请参见 [CRT functions not supported with \/ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)（CRT 函数不支持使用\/ZW）。  
  
## 语法  
  
```  
int _putenv(  
   const char *envstring   
);  
int _wputenv(  
   const wchar_t *envstring   
);  
```  
  
#### 参数  
 `envstring`  
 环境字符串定义。  
  
## 返回值  
 如果成功，返回 0;如果错误，返回– 1 。  
  
## 备注  
 `_putenv` 函数添加新环境变量或修改现有环境变量的值。  环境变量定义进程执行环境 \(例如，可以将库的默认查找路径与程序链接\)。  `_wputenv` 是 `_putenv` 的宽字符版本；`_wputenv` 的 `envstring` 参数是宽字符字符串。  
  
### 一般文本例程映射  
  
|Tchar.h 例程|未定义 \_UNICODE 和 \_MBCS|已定义 \_MBCS|已定义 \_UNICODE|  
|----------------|----------------------------|----------------|-------------------|  
|`_tputenv`|`_putenv`|`_putenv`|`_wputenv`|  
  
 `envstring` 参数必须是指向 `varname=string`窗体字符串的指针，`varname` 是要添加或修改的环境变量名称， `string` 是变量值。  如果 `varname` 已经属于该环境的一部分，其值被`string`替换；否则，新的 `varname`变量 及其 `string` 值被添加到该环境。  也就是说，您可以通过指定空 `string`从该环境移除变量 —换句话说就是通过指定唯一的 `varname=`。  
  
 `_putenv` 和 `_wputenv` 只影响到对于当前进程是本地的环境；不能将这些修改命令级环境。  即这些函数只在可以访问运行库的数据结构运行，而不在由操作系统为进程创建的环境段运行。  在当前进程停止时，环境还原到调用进程级别 \(大多数情况下，操作系统级别\)。  但是，`_spawn`、`_exec`或 `system`创建的新进程可以传递修改的环境，并且，这些新进程获取所有由 `_putenv` 和 `_wputenv`添加的新项。  
  
 不要直接更改环境项：相反，应使用 `_putenv` 或 `_wputenv` 更改它。  具体而言，`_environ[]` 全局数组的直接释放组件可能会导致无效内存被寻址。  
  
 `getenv` 和 `_putenv` 使用全局变量 `_environ` 访问环境表；`_wgetenv` 和 `_wputenv` 使用 `_wenviron`。  `_putenv` 和 `_wputenv` 可能更改 `_environ` 和 `_wenviron`的值，因此无效 `_envp` 参数传递给 `main` ，`wenvp` 参数传递给 `wmain`。  因此，使用 `_environ` 或 `_wenviron` 访问环境信息会更加安全。  有关全局变量`_putenv` 和 `_wputenv` 的关系，请参见 [\_environ，\_wenviron](../../c-runtime-library/environ-wenviron.md)。  
  
> [!NOTE]
>  `_putenv` 和 `_getenv`函数系列不是线程安全的。  `_getenv` 可以返回字符串指针，当 `_putenv` 修改该字符串时，会导致随机崩溃。  确保对这些函数的调用同步。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_putenv`|\<stdlib.h\>|  
|`_wputenv`|\<stdlib.h\> 或 \<wchar.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
 有关如何使用 `_putenv` 的示例，请参见[getenv、\_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [getenv、\_wgetenv](../../c-runtime-library/reference/getenv-wgetenv.md)   
 [\_searchenv、\_wsearchenv](../../c-runtime-library/reference/searchenv-wsearchenv.md)