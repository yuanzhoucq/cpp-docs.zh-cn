---
title: "安全模板重载 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES"
  - "_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT"
  - "安全模板重载"
ms.assetid: 562741d0-39c0-485e-8529-73d740f29f8f
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# 安全模板重载
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

许多 CRT 函数已经不再使用，因此出现了安全性增强的新版本 \(例如，`strcpy_s` 比`strcpy`更安全。\)  CRT 提供模板重载帮助实现更安全的转换。  
  
 例如，这段代码产生一个警告，因为`strcpy` 已弃用：  
  
 `char szBuf[10];`  
  
 `strcpy(szBuf, "test"); // warning: deprecated`  
  
 可以忽略此警告。  定义符号 `_CRT_SECURE_NO_WARNINGS` 来禁止警告或者更新代码使用 `strcpy_s`:  
  
 `char szBuf[10];`  
  
 `strcpy_s(szBuf, 10, "test"); // security-enhanced _s function`  
  
 模板重载提供的其他选项。  定义 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 为 1 ，能够自动调用更安全的标准 CRT 函数的模板重载。  如果 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 为 1，则对代码的更改是必需的。  在后台，调用`strcpy` 将更改为对 `strcpy_s` 的调用，并使用自动提供的大小参数。  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1`  
  
 `...`  
  
 `char szBuf[10];`  
  
 `strcpy(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")`  
  
 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 不影响计数的函数，例如 `strncpy`。  若要在计数函数中启用模板重载，请定义 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 到 1。  但是，在执行之前，请确保代码进行了字符数统计，而不是统计缓冲区的大小\(一个常见错误\)。  此外，如果调用了安全标量，在调用函数后的缓冲区末尾编写null终结器代码是不必要的。  如果需要截断行为，请参见 [\_TRUNCATE](../c-runtime-library/truncate.md)。  
  
> [!NOTE]
>  宏 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 要求还定义 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 为 1。  如果 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 定义为 1 并且`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 定义为 0，应用程序将无法执行任何模板重载。  
  
 定义 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 到 1 能够使用含安全变量的模板重载\(以“\_s”结尾\) 。  在这种情况下，如果 `_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 为 1，则对原始代码进行少量的更改：  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1`  
  
 `...`  
  
 `char szBuf[10];`  
  
 `strcpy_s(szBuf, "test"); // ==> strcpy_s(szBuf, 10, "test")`  
  
 只有函数的名称需要更改 \(添加“\_s”\);模板重载负责提供大小参数。  
  
 默认情况下，`_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES` 和 `_CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES_COUNT` 定义为0\(禁用），`_CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES` 定义为 1 \(已启用\)。  
  
 请注意这些模板只能重载为的静态数组。  动态分配的缓冲区需要其他的源代码更改。  重新访问上面的示例：  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_STANDARD_NAMES 1`  
  
 `...`  
  
 `char *szBuf = (char*)malloc(10);`  
  
 `strcpy(szBuf, "test"); // still deprecated; have to change to`  
  
 `// strcpy_s(szBuf, 10, "test");`  
  
 和这个：  
  
 `#define _CRT_SECURE_CPP_OVERLOAD_SECURE_NAMES 1`  
  
 `...`  
  
 `char *szBuf = (char*)malloc(10);`  
  
 `strcpy_s(szBuf, "test"); // doesn't compile; have to change to`  
  
 `// strcpy_s(szBuf, 10, "test");`  
  
## 请参阅  
 [CRT 中的安全功能](../c-runtime-library/security-features-in-the-crt.md)   
 [CRT 库功能](../c-runtime-library/crt-library-features.md)