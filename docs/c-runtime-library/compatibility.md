---
title: "兼容性 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- CRT, compatibility
- compatibility, C run-time libraries
- compatibility
ms.assetid: 346709cb-edda-4909-9a19-3d253eddb6b7
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bed3ebc3723bfe6af8e3d12fc3702ecb0dda7b4f
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="compatibility"></a>兼容性
通用 C 运行时库 (UCRT) 支持实现 C++ 一致性所需的大多数 C 标准库。 它实现了 C99 (ISO/IEC 9899:1999) 库，\<tgmath.h> 中定义的泛型类型宏和 \<complex.h> 中的严格的类型兼容性除外。 UCRT 还实现了 POSIX.1（ISO/IEC 9945-1:1996，POSIX 系统应用程序编程接口）C 库的大型子集，但不完全符合任何特定的 POSIX 标准。  此外，UCRT 实现了几个特定于 Microsoft 的函数和不属于标准的一部分的宏。  
  
 在 vcruntime 库中找到了特定于 Visual C++ 的 Microsoft 实现的函数。  这些函数中的许多函数都适用于内部使用，且不能通过用户代码调用。 记录了一些函数，以供调试和实现兼容性时使用。  
  
 C++ 标准将全局命名空间中以下划线开头的名称保留到实现中。 因为 POSIX 函数位于全局命名空间中，但不属于标准 C 运行时库的一部分，所以这些函数特定于 Microsoft 的实现具有前导下划线。 为了便于移植，UCRT 还支持默认名称，但是使用它们编译代码时，Visual C++ 编译器会发出弃用警告。 仅会弃用默认的 POSIX 名称，而不会弃用函数。 若要取消警告，在使用原始 POSIX 名称的代码中包含任何标头之前，请定义 `_CRT_NONSTDC_NO_WARNINGS` 。  
  
 由于误用参数和未检查缓冲区，标准 C 库中的某些函数具有不安全的使用情况历史记录。 这些函数通常是代码中出现的安全问题的来源。 Microsoft 创建了这些函数的一组更加安全的版本，在运行时检测到问题时，可用于验证参数的使用情况并调用无效的参数处理程序。  默认情况下，如果使用的函数具有更加安全的变体，Visual C++ 编译器会发出弃用警告。 当编译 C++ 代码时，你可以将 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定义为 1，以消除大多数警告。 这会使用模板重载调用更加安全的变体，同时保持可移植的源代码。 若要取消警告，在使用这些函数的代码中包含任何标头之前，请定义 `_CRT_SECURE_NO_WARNINGS` 。 有关详细信息，请参阅 [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md)。  
  
 除非文档中对特定函数另有注明，否则 UCRT 与 Windows API 可兼容。  某些函数在 Windows 8 应用商店应用或 Windows 10 上的通用 Windows 平台 (UWP) 应用中不受支持。 这些函数都在[通用 Windows 平台应用中不支持的 CRT 函数](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)中列出，其中枚举了 Windows 运行时和 [UWP](/uwp) 不支持的函数。  
  
## <a name="related-articles"></a>相关文章  
  
|标题|描述|  
|-----------|-----------------|  
|[UWP 应用、Windows 运行时和 C 运行时](../c-runtime-library/windows-store-apps-the-windows-runtime-and-the-c-run-time.md)|说明 UCRT 例程何时与通用 Windows 应用或 Microsoft 应用商店应用不兼容。|  
|[ANSI C 遵从性](../c-runtime-library/ansi-c-compliance.md)|说明 UCRT 中符合标准的命名。|  
|[UNIX](../c-runtime-library/unix.md)|提供将程序移植到 UNIX 的指南。|  
|[Windows 平台 (CRT)](../c-runtime-library/windows-platforms-crt.md)|列出 CRT 支持的操作系统。|  
|[向后兼容性](../c-runtime-library/backward-compatibility.md)|描述如何将旧 CRT 名称映射到新名称。|  
|[CRT 库功能](../c-runtime-library/crt-library-features.md)|提供 CRT 库 (.lib) 文件和关联的编译器选项的概述。|