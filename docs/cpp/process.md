---
title: "进程 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Process"
  - "process_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec 关键字 [C++], 进程"
  - "process __declspec 关键字"
ms.assetid: 60eecc2f-4eef-4567-b9db-aaed34733023
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 进程
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指定托管应用程序进程在该过程中应具有特定全局变量、静态成员变量或在任何应用程序域之间共享的静态局部变量的单一副本。  这旨在使用 **\/clr:pure** 编译时使用，因为在 **\/clr:pure** 下，全局和静态变量被默认为每应用程序域。  在使用 **\/clr** 编译时，默认情况下全局和静态变量是每个进程（不需要使用 `__declspec(process)`。）  
  
 只有本机类型的全局变量、静态成员变量或静态局部变量可以使用 `__declspec(process)` 标记。  
  
 在使用 **\/clr:pure** 编译时，还必须将标记为每个进程的变量声明为 `const`。  这可确保每个进程变量在一个应用程序域中不会改变，并且不会在其他应用程序域中生成意外的结果。  `__declspec(process)` 的主要用途是启用全局变量、静态成员变量或 **\/clr:pure** 下的静态局部变量的编译时初始化。  
  
 只有在使用 [\/clr](../build/reference/clr-common-language-runtime-compilation.md) 或 **\/clr:pure** 进行编译时，`process`才是有效性的；在使用 **\/clr:safe** 进行编译时，它是无效的。  
  
 如果希望每个应用程序域都有自己的全局变量副本，请使用 [appdomain](../cpp/appdomain.md)。  
  
 有关更多信息，请参见[应用程序域和 Visual C\+\+](../dotnet/application-domains-and-visual-cpp.md)。  
  
## 请参阅  
 [\_\_declspec](../cpp/declspec.md)   
 [C\+\+ 关键字](../cpp/keywords-cpp.md)