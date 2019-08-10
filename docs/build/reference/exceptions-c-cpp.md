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
ms.openlocfilehash: cf38af464f08e143ed9073befe30f6aeb8b913b6
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915467"
---
# <a name="exceptions-cc"></a>异常 (C/C++)

当遇到失败时, 可以引发两个异常代码:

- 对于**LoadLibrary**失败

- 对于**GetProcAddress**失败

下面是异常信息:

```
//
// Exception information
//
#define FACILITY_VISUALCPP  ((LONG)0x6d)
#define VcppException(sev,err)  ((sev) | (FACILITY_VISUALCPP<<16) | err)
```

引发的异常代码是标准的 VcppException (ERROR_SEVERITY_ERROR、ERROR_MOD_NOT_FOUND) 和 VcppException (ERROR_SEVERITY_ERROR, ERROR_PROC_NOT_FOUND) 值。 此异常将指针传递到 LPDWORD 值中的**DelayLoadInfo**结构, 可通过**GetExceptionInformation**在[EXCEPTION_RECORD](/windows/desktop/api/winnt/ns-winnt-exception_record) structure, ExceptionInformation [0] 字段中进行检索。

此外, 如果在 grAttrs 字段中设置了不正确的位, 则会引发异常 ERROR_INVALID_PARAMETER。 此例外是出于所有意图和目的, 都是致命的。

有关详细信息, 请参阅[结构和常量定义](structure-and-constant-definitions.md)。

## <a name="see-also"></a>请参阅

[错误处理和通知](error-handling-and-notification.md)
