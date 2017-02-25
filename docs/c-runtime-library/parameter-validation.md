---
title: "参数验证 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "参数, 验证"
ms.assetid: 019dd5f0-dc61-4d2e-b4e9-b66409ddf1f2
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 参数验证
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

大多数安全系数高的 CRT 函数和许多现有函数验证它们的参数。  这包括检查空指针，检查整数是否落入有效的范围，或检查枚举该值是否有效。  当找到无效参数时，将执行无效参数处理程序。  
  
## 无效参数处理程序实例  
 当发现无效参数时，C 运行时会调用当前分配的参数无效处理程序。  默认无效参数调用 Watson 失败报告，导致应用程序崩溃并询问用户他们是否要为了分析将加载故障转储到 Microsoft。  在调试模式下，无效参数还导致不合格的断言。  
  
 此行为可能被更改，通过使用函数 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 设置参数无效处理程序到自己的函数。  如果指定的函数不终止应用程序，控件返回到接收无效参数的函数，并且，这些函数通常将停止执行，返回错误代码并设置 `errno` 为错误代码。  在许多情况下，`errno` 值和返回值都是 `EINVAL`，指示参数无效。  有时，更具体的错误代码返回，例如，作为参数传递的一个错误文件指针的 `EBADF`。  有关错误的更多信息，请参见 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 请参阅  
 [CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)   
 [CRT 库功能](../c-runtime-library/crt-library-features.md)