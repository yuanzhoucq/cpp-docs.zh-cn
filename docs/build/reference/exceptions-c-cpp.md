---
title: 异常 （C/c + +） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
dev_langs:
- C++
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 819f9424b2439cc49517afe54d62a8ed4f06d22d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32373382"
---
# <a name="exceptions-cc"></a>异常 (C/C++)
遇到故障时，可以引发两个异常代码：  
  
-   有关**LoadLibrary**失败  
  
-   有关**GetProcAddress**失败  
  
 下面是异常信息：  
  
```  
//  
// Exception information  
//  
#define FACILITY_VISUALCPP  ((LONG)0x6d)  
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)  
```  
  
 引发的异常代码为标准 VcppException （ERROR_SEVERITY_ERROR，ERROR_MOD_NOT_FOUND），VcppException （ERROR_SEVERITY_ERROR，ERROR_PROC_NOT_FOUND） 值。 异常将传递指向的指针**DelayLoadInfo**中可以通过检索 LPDWORD 值结构**GetExceptionInformation**中[EXCEPTION_RECORD](http://msdn.microsoft.com/library/windows/desktop/aa363082)结构，ExceptionInformation [0] 字段。  
  
 此外，如果 grAttrs 字段中设置不正确的位、 ERROR_INVALID_PARAMETER 是引发异常。 此异常是出于何种目的，致命的。  
  
 请参阅[结构和常量定义](../../build/reference/structure-and-constant-definitions.md)有关详细信息。  
  
## <a name="see-also"></a>请参阅  
 [错误处理和通知](../../build/reference/error-handling-and-notification.md)