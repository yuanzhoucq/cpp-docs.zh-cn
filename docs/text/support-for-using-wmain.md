---
title: "支持使用 wmain | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "wWinMain"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "宽字符 [C++], wmain 函数"
  - "wmain 函数"
  - "wWinMain 函数"
ms.assetid: 41213c41-668c-40a4-8a1e-77d9eded720d
caps.latest.revision: 9
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 9
---
# 支持使用 wmain
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 支持定义 **wmain** 函数，并将宽字符参数传递给 Unicode 应用程序。  使用与 **main** 函数相似的格式声明 **wmain** 函数的形参。  然后可以将宽字符参数和宽字符环境指针（可选）传递给该程序。  **wmain** 的 `argv` 和 `envp` 参数为 `wchar_t*` 类型。  例如：  
  
```  
wmain( int argc, wchar_t *argv[ ], wchar_t *envp[ ] )  
```  
  
> [!NOTE]
>  MFC Unicode 应用程序使用 **wWinMain** 作为入口点。  在这种情况下，`CWinApp::m_lpCmdLine` 是一个 Unicode 字符串。  请务必使用 [\/ENTRY](../build/reference/entry-entry-point-symbol.md) 链接器选项设置 **wWinMainCRTStartup**。  
  
 如果程序使用 **main** 函数，则多字节字符环境由运行库在程序启动时创建。  环境的宽字符副本仅在需要时创建（如调用 `_wgetenv` 或 `_wputenv` 函数时）。  首次调用 `_wputenv` 或在 MBCS 环境已存在的情况下首次调用 `_wgetenv` 时，将创建相应的宽字符字符串环境。  然后用 `_wenviron` 全局变量（`_environ` 全局变量的宽字符版本）指向该环境。  此时，同时存在两个环境的副本（MBCS 和 Unicode），在程序的整个生存期这两个副本由运行时系统维护。  
  
 同样，如果程序使用 **wmain** 函数，则在程序启动时创建宽字符环境并用 `_wenviron` 全局变量指向该环境。  在首次调用 `_putenv` 或 `getenv` 时创建 MBCS \(ASCII\) 环境，并用 `_environ` 全局变量指向该环境。  
  
## 请参阅  
 [支持 Unicode](../text/support-for-unicode.md)   
 [Unicode 编程摘要](../text/unicode-programming-summary.md)   
 [WinMain 函数](http://msdn.microsoft.com/library/windows/desktop/ms633559)