---
title: "错误处理 (CRT) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.errors
dev_langs: C++
helpviewer_keywords:
- error handling, C routines for
- logic errors
- error handling, library routines
- testing, for program errors
ms.assetid: 125ac697-9eb0-4152-a440-b7842f23d97f
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f40b2deb5c78667e5343bd2be0948252e2f2e154
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="error-handling-crt"></a>错误处理 (CRT)
使用这些例程处理程序错误。  
  
### <a name="error-handling-routines"></a>错误处理例程  
  
|例程所返回的值|使用|  
|-------------|---------|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md) 宏|测试编程逻辑错误；在运行时库的发行版和调试版中可用。|  
|[_ASSERT、_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 宏|类似于 `assert`，但仅在运行时库的调试版本中可用。|  
|[clearerr](../c-runtime-library/reference/clearerr.md)|重置错误指示器。 调用 `rewind` 或关闭流也会重置错误指示器。|  
|[_eof](../c-runtime-library/reference/eof.md)|检查底层 I/O 的文件尾。|  
|[feof](../c-runtime-library/reference/feof.md)|测试文件尾。 当 `_read` 返回 0 时，也指示文件尾。|  
|[ferror](../c-runtime-library/reference/ferror.md)|测试流 I/O 错误。|  
|[_RPT、_RPTF](../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) 宏|生成类似于 `printf` 的报告，但仅在运行时库的调试版本中可用。|  
|[_set_error_mode](../c-runtime-library/reference/set-error-mode.md)|修改 `__error_mode` 来确定非默认位置，其中，C 运行时为可能导致程序关闭的错误编写错误消息。|  
|[_set_purecall_handler](../c-runtime-library/reference/get-purecall-handler-set-purecall-handler.md)|为纯虚函数调用设置处理程序。|  
  
## <a name="see-also"></a>请参阅  
 [按类别分的运行时例程](../c-runtime-library/run-time-routines-by-category.md)