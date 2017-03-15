---
title: "_set_error_mode | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_set_error_mode"
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
  - "set_error_mode"
  - "_set_error_mode"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_set_error_mode 函数"
  - "set_error_mode 函数"
ms.assetid: f0807be5-73d1-4a32-a701-3c9bdd139c5c
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# _set_error_mode
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

修改 `__error_mode` 可确定供 C 运行时为可能终止程序的错误编写错误信息的非默认位置。  
  
> [!IMPORTANT]
>  此 API 不能用于在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中执行的应用程序。  有关详细信息，请参阅 [\/ZW 不支持 CRT 函数](http://msdn.microsoft.com/ZH-CN/library/windows/apps/jj606124.aspx)。  
  
## 语法  
  
```  
int _set_error_mode(  
   int modeval   
);  
```  
  
#### 参数  
 `modeval`  
 错误消息的目标。  
  
## 返回值  
 如果出现错误，则返回旧设置或 \-1。  
  
## 备注  
 通过设置 `__error_mode` 的值来控制错误输出接收器。  例如，您可将输出指向标准错误或使用 `MessageBox` API。  
  
 `modeval` 参数可设置为下列值之一。  
  
|参数|描述|  
|--------|--------|  
|`_OUT_TO_DEFAULT`|`__app_type` 确定错误接收器。|  
|`_OUT_TO_STDERR`|错误接收器是一个标准错误。|  
|`_OUT_TO_MSGBOX`|错误接收器是一个消息框。|  
|`_REPORT_ERRMODE`|报告当前 `__error_mode` 值。|  
  
 如果传入所列出的值之外的值，则将调用无效的参数处理程序，如[参数验证](../../c-runtime-library/parameter-validation.md)中所述。  如果允许执行继续，则 `_set_error_mode` 会将 `errno` 设置为 `EINVAL` 并返回 \-1。  
  
 在将其与 [assert](../../c-runtime-library/reference/assert-macro-assert-wassert.md) 一起使用时，`_set_error_mode` 会在对话框中显示失败的语句，并是您能够选择 `Ignore` 按钮以便继续运行程序。  
  
## 要求  
  
|例程|必需的标头|  
|--------|-----------|  
|`_set_error_mode`|\<stdlib.h\>|  
  
## 示例  
  
```  
// crt_set_error_mode.c  
// compile with: /c  
#include <stdlib.h>  
#include <assert.h>  
  
int main()  
{  
   _set_error_mode(_OUT_TO_STDERR);  
   assert(2+2==5);  
}  
```  
  
  **Assertion failed: 2\+2\=\=5, file crt\_set\_error\_mode.c, line 8**  
**This application has requested the Runtime to terminate it in an unusual way.  Please contact the application's support team for more information.**    
## 请参阅  
 [assert 宏、\_assert、\_wassert](../../c-runtime-library/reference/assert-macro-assert-wassert.md)