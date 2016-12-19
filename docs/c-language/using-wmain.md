---
title: "使用 wmain | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "wmain 函数"
ms.assetid: d0300812-adc4-40c6-bba3-b2da25468c80
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用 wmain
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 专用**  
  
 在 Unicode 编程模型中，可以定义 **main** 函数的宽字符版本。  如果要编写符合 Unicode 编程模型的可移植代码，请使用 **wmain** 而不是 **main**。  
  
## 语法  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
## 备注  
 使用与 **main** 的相似格式声明 **wmain** 的形参。  然后可以将宽字符参数和宽字符环境指针（可选）传递给该程序。  **wmain** 的 `argv` 和 `envp` 参数为 `wchar_t*` 类型。  例如：  
  
 如果程序使用 **main** 函数，则多字节字符环境由运行库在程序启动时创建。  环境的宽字符副本仅在需要时创建（如调用 `_wgetenv` 或 `_wputenv` 函数时）。  在首次调用 `_wputenv` 或首次调用 `_wgetenv` 时（如果 MBCS 环境已存在），会创建一个对应的宽字符字符串环境，然后通过 `_wenviron` 全局变量指向该环境，此变量是 `_environ` 全局变量的宽字符版本。  此时，同时存在该环境的两个副本（MBCS 和 Unicode），在程序的整个生存期这两个副本由操作系统维护。  
  
 同样，如果程序使用 **wmain** 函数，则在程序启动时创建宽字符环境并用 `_wenviron` 全局变量指向该环境。  MBCS \(ASCII\) 环境是在首次调用 `_putenv` 或 `getenv` 时创建的，并由 `_environ` 全局变量指向。  
  
 有关 MBCS 环境的详细信息，请参阅《运行时库参考》中的[国际化](../c-runtime-library/internationalization.md)。  
  
 **结束 Microsoft 专用**  
  
## 请参阅  
 [main 函数和程序执行](../c-language/main-function-and-program-execution.md)