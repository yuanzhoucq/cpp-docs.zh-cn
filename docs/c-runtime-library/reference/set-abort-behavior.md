---
title: "_set_abort_behavior | Microsoft Docs"
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
  - "_set_abort_behavior"
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
  - "_set_abort_behavior"
  - "set_abort_behavior"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_set_abort_behavior 函数"
  - "中止程序"
  - "set_abort_behavior 函数"
ms.assetid: 43918766-e4ba-4b1f-80e8-1a4a910cd452
caps.latest.revision: 26
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _set_abort_behavior
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

当程序异常终止时，指定要执行的操作。  
  
> [!NOTE]
>  不要使用 `abort` 函数关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序，除非在测试或调试方案中。  根据 [Windows 8 应用程序证书要求](http://go.microsoft.com/fwlink/?LinkId=262889)，禁止以编程或 UI 方式关闭 [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)] 应用程序。  有关详情，请参阅[应用程序生命周期（Windows 应用商店应用）](http://go.microsoft.com/fwlink/?LinkId=262853)。  
  
## 语法  
  
```  
unsigned int _set_abort_behavior(  
   unsigned int flags,  
   unsigned int mask  
);  
```  
  
#### 参数  
 \[in\] `flags`  
 `abort` 标志的新值。  
  
 \[in\] `mask`  
 要设置的 `abort` 标志的掩码。  
  
## 返回值  
 该标志的旧值。  
  
## 备注  
 有两种 `abort` 标志：`_WRITE_ABORT_MSG` 和 `_CALL_REPORTFAULT`。  当程序异常终止时，`_WRITE_ABORT_MSG` 确定是否打印一个有用的文本消息。  消息声明应用程序调用 `abort` 函数。  默认行为是打印消息。  `_CALL_REPORTFAULT`，如果设置，当调用 `abort` 时，指定 Watson 崩溃转储生成并报告   默认情况下，崩溃转储报告在非调试生成中启用。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_abort_behavior`|\<stdlib.h\>|  
  
 有关更多兼容性信息，请参见[兼容性](../../c-runtime-library/compatibility.md)。  
  
## 示例  
  
```c  
// crt_set_abort_behavior.c  
// compile with: /TC  
#include <stdlib.h>  
  
int main()  
{  
   printf("Suppressing the abort message. If successful, this message"  
          " will be the only output.\n");  
   // Suppress the abort message  
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);  
   abort();  
}  
```  
  
  **禁止显示中止消息。  如果成功，此消息将成为唯一的输出。**    
## 请参阅  
 [abort](../../c-runtime-library/reference/abort.md)