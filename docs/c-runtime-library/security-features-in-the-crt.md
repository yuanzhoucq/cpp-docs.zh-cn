---
title: "CRT 中的安全功能 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _CRT_SECURE_NO_DEPRECATE
- _CRT_NONSTDC_NO_WARNINGS
- _CRT_SECURE_NO_WARNINGS
dev_langs:
- C++
helpviewer_keywords:
- security deprecation warnings [C++]
- CRT_NONSTDC_NO_DEPRECATE
- buffers [C++], buffer overruns
- deprecation warnings (security-related), disabling
- _CRT_NONSTDC_NO_WARNINGS
- security [CRT]
- _CRT_SECURE_NO_WARNINGS
- _CRT_NONSTDC_NO_DEPRECATE
- _CRT_SECURE_NO_DEPRECATE
- security-enhanced CRT
- CRT_SECURE_NO_WARNINGS
- CRT_SECURE_NO_DEPRECATE
- deprecation warnings (security-related)
- buffer overruns
- CRT_NONSTDC_NO_WARNINGS
- CRT, security enhancements
- parameters [C++], validation
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: c197434fceff8920cd501a64131c3e0816c9594d
ms.contentlocale: zh-cn
ms.lasthandoff: 05/18/2017

---
# <a name="security-features-in-the-crt"></a>CRT 中的安全功能
许多旧 CRT 函数具有更新、更安全的版本。 如果存在安全函数，则较旧的、安全性更低的版本将标记为已弃用，并且新版本具有 `_s`（“安全”）后缀。  
  
 在此上下文中，“已弃用”仅表示不建议使用某个函数；而不表示计划从 CRT 中删除此函数。  
  
 安全函数不阻止或纠正安全性错误，而是在出现错误时捕获错误。 它们对错误条件进行附加检查，如果出现错误，它们将调用错误处理程序（请参阅[参数验证](../c-runtime-library/parameter-validation.md)）。  
  
 例如，`strcpy` 函数无法指明它所复制的字符串对于目标缓冲区是否太大。 但是，它的安全匹配项 `strcpy_s` 可将缓冲区大小作为参数，以便确定是否将发生缓冲区溢出。 如果您使用 `strcpy_s` 将 11 个字符复制到 10 字符缓冲区中，那么就是您做错了；`strcpy_s` 无法纠正您的错误，但它可检测到您的错误，并通过调用无效参数处理程序来告知您此情况。  
  
## <a name="eliminating-deprecation-warnings"></a>消除弃用警告  
 可通过多种方式消除针对较旧的、安全性更低的函数的弃用警告。 最简单的方法是定义 `_CRT_SECURE_NO_WARNINGS` 或使用[警告](../preprocessor/warning.md)杂注。 这将禁用弃用警告，但导致出现警告的安全问题仍存在。 更佳的做法是，将弃用警告保持启用状态并利用新的 CRT 安全功能。  
  
 在 C++ 中，执行此操作的最简单方法是使用[安全模板重载](../c-runtime-library/secure-template-overloads.md)，在许多情况下，它会通过将对已弃用函数的调用替换为对这些函数的新安全版本的调用来消除弃用警告。 例如，考虑此对 `strcpy` 的已弃用调用：  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 将 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定义为 1 可通过将 `strcpy` 调用更改为 `strcpy_s`（这将阻止缓冲区溢出）来消除警告。 有关详细信息，请参阅 [Secure Template Overloads](../c-runtime-library/secure-template-overloads.md)。  
  
 对于那些不带安全模板重载的已弃用的函数，你应考虑手动更新代码以使用安全版本。  
  
 弃用警告的另一个源（与安全性无关）为 POSIX 函数。 将 POSIX 函数名称替换为它们的标准等效项（例如，将 [access](../c-runtime-library/reference/access-crt.md) 更改为 [_access](../c-runtime-library/reference/access-waccess.md)），或通过定义 `_CRT_NONSTDC_NO_WARNINGS` 来禁用与 POSIX 相关的弃用警告。 有关详细信息，请参阅[弃用的 CRT 函数](http://msdn.microsoft.com/en-us/7e259932-c6c8-4c1a-9637-639e591681a5)。  
  
## <a name="additional-security-features"></a>其他安全功能  
 一些安全功能包括：  
  
-   `Parameter Validation`。 在安全函数和许多先前已有的函数版本中验证传递到 CRT 函数的参数。 这些验证包括：  
  
    -   检查已传递到函数的 `NULL` 值。  
  
    -   检查枚举值的有效性。  
  
    -   检查整数值是否在有效范围内。  
  
-   有关详细信息，请参阅[参数验证](../c-runtime-library/parameter-validation.md)。  
  
-   开发人员也可访问无效参数的处理程序。 当遇到无效参数时，CRT 提供使用 [_set_invalid_parameter_handler, _set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 函数检查这些问题的方法，而不是断言并退出应用程序。  
  
-   `Sized Buffers`。 安全函数要求将缓冲区大小传递到对缓冲区进行写入操作的任何函数。 安全版本会在对缓冲区进行写入之前先验证它是否足够大，以帮助避免导致恶意代码能够执行的危险缓冲区溢出错误。 这些函数通常返回一个 `errno` 类型的错误代码并调用无效参数处理程序（如果缓冲区太小）。 从输入缓冲区读取的函数（如 `gets`）具有需要您指定最大大小的安全版本。  
  
-   `Null termination`。 某些可能保留非终止字符串的函数具有安全版本，这将确保字符串以 null 结束。  
  
-   `Enhanced error reporting`。 安全函数将返回错误代码以及比先前存在的函数返回的错误信息更多的错误信息。 安全函数和许多先前存在的函数现在可设置 `errno`，并且通常会返回 `errno` 代码类型，以便提供更好的错误报告。  
  
-   `Filesystem security`。 默认情况下，安全文件 I/O API 支持安全文件访问。  
  
-   `Windows security`。 安全进程 API 强制安全策略并允许指定 ACL。  
  
-   `Format string syntax checking`。 检测到无效字符串，例如，在 `printf` 格式字符串中使用了不正确的类型字段字符。  
  
## <a name="see-also"></a>另请参阅  
 [参数验证](../c-runtime-library/parameter-validation.md)   
 [安全模板重载](../c-runtime-library/secure-template-overloads.md)   
 [CRT 库功能](../c-runtime-library/crt-library-features.md)
