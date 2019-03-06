---
title: 异常 (C/C++)
ms.date: 11/04/2016
f1_keywords:
- ERROR_MOD_NOT_FOUND
- vcppException
- ERROR_SEVERITY_ERROR
helpviewer_keywords:
- vcppException
- C++ exception handling, delayed loading of DLLs
- delayed loading of DLLs, exceptions
- ERROR_SEVERITY_ERROR exception
- ERROR_MOD_NOT_FOUND exception
ms.assetid: c03be05d-1c39-4f35-84cf-00c9af3bae9a
ms.openlocfilehash: 9c86d99b365994870b991967b6cab6e6ee5c5088
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/05/2019
ms.locfileid: "57422983"
---
# <a name="exceptions-cc"></a>异常 (C/C++)

遇到故障时，可以引发两个异常代码：

- 有关**LoadLibrary**失败

- 有关**GetProcAddress**失败

下面是异常信息：

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

引发的异常代码是标准 VcppException （ERROR_SEVERITY_ERROR，ERROR_MOD_NOT_FOUND） 和 VcppException （ERROR_SEVERITY_ERROR，ERROR_PROC_NOT_FOUND） 值。 异常将传递一个指向**DelayLoadInfo**来检索 LPDWORD 值中的结构**GetExceptionInformation**中[EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-_exception_record)结构，ExceptionInformation [0] 字段。

此外，如果不正确的位将设置 grAttrs 字段中，ERROR_INVALID_PARAMETER 是引发异常。 此异常是用于所有目的和用途，致命的。

请参阅[结构和常量定义](../../build/reference/structure-and-constant-definitions.md)有关详细信息。

## <a name="see-also"></a>请参阅

[错误处理和通知](../../build/reference/error-handling-and-notification.md)
