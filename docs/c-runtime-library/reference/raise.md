---
title: "raise | Microsoft Docs"
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
  - "raise"
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
  - "api-ms-win-crt-runtime-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "Raise"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "程序 [C++], 向正在执行的程序发送信号"
  - "raise 函数"
  - "信号"
  - "信号, 发生到正在执行的程序"
ms.assetid: a3ccd3ad-f68f-4a7b-a005-c3ebfb217e8b
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# raise
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

发送信号给执行程序。  
  
> [!NOTE]
>  不要使用此方法关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序，除非在测试或调试方案中。  根据 [Windows 8 应用程序证书要求](http://go.microsoft.com/fwlink/?LinkId=262889)的3.6节，禁止以编程或 UI 方式关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序。  有关详情，请参阅[应用程序生命周期（Windows 应用商店应用）](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 语法  
  
```  
  
      int raise(  
int sig   
);  
```  
  
#### 参数  
 *sig*  
 引发信号。  
  
## 返回值  
 如果成功，**raise** 返回 0。  否则，它返回一个非零值。  
  
## 备注  
 **raise**函数发送 *信号* 到执行程序。  如果以前调用了为*sig*装有信号处理函数 的**信号** ，**raise** 执行该函数。  如果未安装处理程序函数，默认值操作与信号 *通知* 采用值相关，如下所示。  
  
|Signal|含义|默认|  
|------------|--------|--------|  
|`SIGABRT`|Abnormal termination|停止调用的程序以退出代码 3|  
|`SIGFPE`|浮点错误|终止调用程序|  
|`SIGILL`|非法指令|终止调用程序|  
|`SIGINT`|CTRL\+C 中断|终止调用程序|  
|`SIGSEGV`|非法存储区访问|终止调用程序|  
|`SIGTERM`|停止请求发送到程序|忽略信号|  
  
 如上所述如果参数不是有效的信号，无效参数调用处理程序，如 [参数验证](../../c-runtime-library/parameter-validation.md)所述。  如果未处理，函数设置 `errno` 为 `EINVAL` 并返回一个非零值。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|**raise**|\<signal.h\>|  
  
 有关兼容性的更多信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 库  
 [C 运行时库](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## .NET Framework 等效项  
 不适用。若要调用标准 C 函数，请使用 `PInvoke`。有关更多信息，请参见[平台调用示例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 请参阅  
 [进程和环境控制](../../c-runtime-library/process-and-environment-control.md)   
 [abort](../../c-runtime-library/reference/abort.md)   
 [signal](../../c-runtime-library/reference/signal.md)