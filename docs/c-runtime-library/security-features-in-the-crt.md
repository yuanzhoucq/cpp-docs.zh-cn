---
title: "CRT 中的安全功能 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_CRT_SECURE_NO_DEPRECATE"
  - "_CRT_NONSTDC_NO_WARNINGS"
  - "_CRT_SECURE_NO_WARNINGS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_NONSTDC_NO_DEPRECATE"
  - "_CRT_NONSTDC_NO_WARNINGS"
  - "_CRT_SECURE_NO_DEPRECATE"
  - "_CRT_SECURE_NO_WARNINGS"
  - "缓冲区溢出"
  - "缓冲区 [C++], 缓冲区溢出"
  - "CRT, 安全性增强功能"
  - "CRT_NONSTDC_NO_DEPRECATE"
  - "CRT_NONSTDC_NO_WARNINGS"
  - "CRT_SECURE_NO_DEPRECATE"
  - "CRT_SECURE_NO_WARNINGS"
  - "否决警告（与安全相关）"
  - "否决警告（与安全相关）, 禁用"
  - "参数 [C++], 验证"
  - "安全性 [CRT]"
  - "安全否决警告 [C++]"
  - "增强了安全性的 CRT"
ms.assetid: d9568b08-9514-49cd-b3dc-2454ded195a3
caps.latest.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 23
---
# CRT 中的安全功能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多以前 CRT 函数具有较新，更安全版本。  如果安全函数存在，旧，较不安全版本标记为弃和新版本具有 `_s` \(“保护”\) 后缀。  
  
 在此上下文中，“用”表示不建议函数的使用；它指出该函数不计划从 CRT 中移除。  
  
 安全函数不阻止或正确的安全性错误；相比之下，一旦发生时，将看到错误。  它们执行附加的检查错误条件，并且，对于错误，它们称为错误处理程序 \(请参见\)。[参数验证](../c-runtime-library/parameter-validation.md)  
  
 例如，`strcpy` 函数不能调用字符串复制它是否为其目标缓冲区太大的。  但是，它的安全副本，`strcpy_s`，将缓冲区大小作为参数，因此，它可以确定是否发生缓冲区溢出。  如果使用 `strcpy_s` 将字符放到一个十六进制字符缓冲区，这是在部分中有错误；`strcpy_s` 不可以更正错误，但是，它可以检测错误和通过调用的参数无效处理程序会通知您。  
  
## 对象消除警告  
 有多种方法清除之前的、较不安全函数的对象警告。  最简单的形式是定义 `_CRT_SECURE_NO_WARNINGS` 或使用杂注。[警告](../preprocessor/warning.md) 或将禁用对象警告，当然仍然应生成警告存在的安全问题。  保持对象警告启用和利用新的安全 CRT 功能最好。  
  
 在 C\+\+ 中，是使用 [安全模板重载](../c-runtime-library/secure-template-overloads.md)，通过替换调用大多数情况下对象消除警告对被否决的函数的调用。这些新函数的安全版本的简单方法执行。  例如，请考虑此被否决的对 `strcpy`的调用：  
  
```  
char szBuf[10];   
strcpy(szBuf, "test"); // warning: deprecated   
```  
  
 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定义为 1 来更改调用 `strcpy` 消除警告为 `strcpy_s`，以避免缓冲区溢出。  有关更多信息，请参见[安全模板重载](../c-runtime-library/secure-template-overloads.md)。  
  
 对于无这些已弃用的保证重载函数中模板，您应该考虑显式手动更新代码使用安全版本。  
  
 否决警告其他源，与无关安全性，POSIX 是函数。  用其标准替换等效 POSIX 函数名称 \(例如，设置为 [\_access](../c-runtime-library/reference/access-waccess.md)[访问](../c-runtime-library/reference/access-crt.md) \) 的更改，或者通过定义 `_CRT_NONSTDC_NO_WARNINGS`禁用 POSIX 对象关联的警告。  有关详细信息，请参阅[Deprecated CRT Functions](http://msdn.microsoft.com/zh-cn/7e259932-c6c8-4c1a-9637-639e591681a5)。  
  
## 其他安全特征  
 下面是一个包含某些安全功能的列表。  
  
-   `Parameter Validation`.  参数在两个传递到 CRT 函数验证，获得函数和函数在许多现有版本。  包括这些验证：  
  
    -   检查 `NULL` 的值传递到函数。  
  
    -   检查有效性的枚举值。  
  
    -   检查整数值在有效范围内。  
  
-   有关详细信息，请参阅[参数验证](../c-runtime-library/parameter-validation.md)。  
  
-   无效参数的处理程序为开发人员也可以访问。  当遇到无效的参数，而不是断言和退出应用程序，CRT 时提供了一种检查与 [\_set\_invalid\_parameter\_handler \_set\_thread\_local\_invalid\_parameter\_handler](../c-runtime-library/reference/set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) 这些问题的函数。  
  
-   `Sized Buffers`.  安全函数需要缓冲区大小传递到写入缓冲区的函数。  安全版本验证缓冲区在之前编写足够大到它，以帮助避免可能允许恶意代码执行的危险缓冲区溢出错误。  如果缓冲区的大小太小，这些函数通常返回错误代码的 `errno` 类型并调用的参数无效处理程序。  从输入缓冲区读取，如 `gets`的函数，则需要指定最大大小的安全版本。  
  
-   `Null termination`.  保留可能非终止的字符串的一些函数有确保的安全版本正确以 Null 终止的字符串。  
  
-   `Enhanced error reporting`.  与一个或多个错误信息的安全函数返回错误代码比适用于现有函数。  安全函数和许多现有函数现在设置 `errno` 和 `errno` 通常返回代码类型，提供更好的报告错误。  
  
-   `Filesystem security`.  安全默认情况下在的文件 I\/O API 支持安全文件访问权限。  
  
-   `Windows security`.  安全处理 API 强制安全策略允许指定 ACL。  
  
-   `Format string syntax checking`.  使用 `printf` 格式字符串，不正确的字段类型字符无效的字符串被检测，例如。  
  
## 请参阅  
 [参数验证](../c-runtime-library/parameter-validation.md)   
 [安全模板重载](../c-runtime-library/secure-template-overloads.md)   
 [CRT 库功能](../c-runtime-library/crt-library-features.md)