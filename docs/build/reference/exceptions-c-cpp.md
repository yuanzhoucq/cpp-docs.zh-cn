---
title: DLL 加载异常代码（C/C++）
ms.date: 11/19/2019
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
ms.openlocfilehash: f557fe736f45f8c3f5411d076a0be18f1d1b670e
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/20/2019
ms.locfileid: "74243850"
---
# <a name="exceptions-cc"></a>异常 (C/C++)

当遇到失败时，可以引发两个异常代码：

- 对于**LoadLibrary**失败

- 对于**GetProcAddress**失败

下面是异常信息：

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

引发的异常代码为标准 VcppException （ERROR_SEVERITY_ERROR、ERROR_MOD_NOT_FOUND）和 VcppException （ERROR_SEVERITY_ERROR，ERROR_PROC_NOT_FOUND）值。 此异常将指针传递到 LPDWORD 值中的**DelayLoadInfo**结构，可通过**GetExceptionInformation**在[EXCEPTION_RECORD](/windows/win32/api/winnt/ns-winnt-exception_record)结构 ExceptionInformation [0] 字段中检索。

此外，如果在 grAttrs 字段中设置了不正确的位，则会引发异常 ERROR_INVALID_PARAMETER。 此例外是出于所有意图和目的，都是致命的。

有关详细信息，请参阅[结构和常量定义](structure-and-constant-definitions.md)。

## <a name="see-also"></a>另请参阅

[错误处理和通知](error-handling-and-notification.md)
