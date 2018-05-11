---
title: 参数验证 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parameters, validation
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a89ec2cd0b360f498e52af7e49bd5c6571521e2c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="parameter-validation"></a>参数验证
大多数安全性增强的 CRT 函数和很多已有的函数都会验证其参数。 这可能包括检指针是否为 NULL、检查整数在有效的范围内或检查枚举该值是否有效。 当发现无效参数时，将执行无效参数处理程序。  
  
## <a name="invalid-parameter-handler-routine"></a>无效参数处理程序例程  
 当 C 运行时库函数检测到无效参数时，会捕获一些错误相关信息，然后调用一个宏来包装 [_invalid_parameter](../c-runtime-library/reference/invalid-parameter-functions.md)、[_invalid_parameter_noinfo](../c-runtime-library/reference/invalid-parameter-functions.md)，或 [_invalid_parameter_noinfo_noreturn](../c-runtime-library/reference/invalid-parameter-functions.md) 中的一个无效参数处理程序调度函数。 调用的调度函数取决于你的代码是否分别为调试版本、零售版本，或错误是否被视为不可恢复。 
 
 在调试版本中，在调用调度函数之前，无效参数宏通常会引发失败断言和调试器断点。 执行代码时，可能会向具有“中止”、“重试”和“继续”或类似选项的对话框中的用户报告断言，具体取决于操作系统和运行时库版本。 这些选项允许用户立即终止程序、附加调试器，或允许调用调度函数的现有代码继续运行。 
 
 无效参数处理程序调度函数反过来调用当前分配的无效参数处理程序。 默认情况下，无效参数调用 `_invoke_watson` 将导致应用程序“故障”，也就是说，终止和生成小型转储。 如果由操作系统启用，对话框会询问用户是否想要将故障转储加载到 Microsoft 进行分析。   
  
 此行为可以通过使用函数 [_set_invalid_parameter_handler ](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 或 [_set_thread_local_invalid_parameter_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 进行更改，将无效参数处理程序设置为你自己的函数。 如果指定的函数未终止应用程序，控制权就会返回至已接收无效参数的函数处。 在 CRT 中，这些函数通常会停止函数执行，向错误代码设置 `errno`，并返回错误代码。 在很多情况下，`errno` 值和返回值都是 `EINVAL`，这指示参数无效。 有时候会返回更具体的错误代码，如作为参数传递的错误的文件指针的 `EBADF`。 有关 `errno` 的详细信息，请参阅 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="see-also"></a>请参阅  
 [CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)   
 [CRT 库功能](../c-runtime-library/crt-library-features.md)