---
title: "自定义 C 命令行处理 | Microsoft Docs"
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
  - "_exec 函数"
  - "_setargv 函数"
  - "_spawn 函数"
  - "命令行, 处理"
  - "命令行, 处理参数"
  - "命令行处理"
  - "环境, 环境处理例程"
  - "启动代码, 自定义命令行处理"
  - "禁止显示环境处理"
ms.assetid: c20fa11d-b35b-4f3e-93b6-2cd5a1c3c993
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自定义 C 命令行处理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果程序不采用命令行参数，则可以通过取消使用执行命令行处理的库例程来节省少量空间。  此例程称为 **\_setargv**（在宽字符环境中，称为 **\_wsetargv**），如[展开通配符参数](../c-language/expanding-wildcard-arguments.md)中所述。  若要禁止使用它，请在包含 **main** 函数的文件中定义一个不执行任何操作的例程，并将其命名为 **\_setargv**（在宽字符环境中为 **\_wsetargv**）。  随后，对 **\_setargv** 或 **\_wsetargv** 的调用由 **\_setargv** 或 **\_wsetargv** 的定义实现，并且不会加载库版本。  
  
 同样，如果您从不通过 `envp` 参数访问环境表，则可以提供用来代替 **\_setenvp**（或 **\_wsetenvp**）的您自己的空例程（环境处理例程）。  
  
 如果您的程序在 C 运行库中调用 **\_spawn** 或 **\_exec** 系列例程，则不应停止环境处理例程，因为需使用此例程将环境从生成进程传递到新进程。  
  
## 请参阅  
 [main 函数和程序执行](../c-language/main-function-and-program-execution.md)