---
title: "应用程序域和 Visual C++ | Microsoft Docs"
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
helpviewer_keywords: 
  - "/clr 编译器选项 [C++], 应用程序域"
  - "应用程序域 [C++], C++"
  - "互操作 [C++], 应用程序域"
  - "互操作性 [C++], 应用程序域"
  - "混合程序集 [C++], 应用程序域"
ms.assetid: 75a08efc-9b02-40ba-99b7-dcbd71010bbf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 应用程序域和 Visual C++
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果具有一个 `__clrcall` 虚函数，vtable 将是基于每应用程序域 \(appdomain\) 的。  如果在某个 Appdomain 中创建对象，您只可以从该 Appdomain 内调用虚函数。  在 **\/clr:pure** compiland 中定义的所有函数使用 `__clrcall` 调用约定。  因此，在 **\/clr:pure** compiland 中定义的所有 vtable 都是单 appdomain。  在混合模式 \(**\/clr**\) 中，如果类型没有 `__clrcall` 虚函数，则将具有单进程 vtable。  
  
 有关更多信息，请参见  
  
-   [appdomain](../cpp/appdomain.md)  
  
-   [\_\_clrcall](../cpp/clrcall.md)  
  
-   [如何：迁移到 \/clr:pure](../dotnet/how-to-migrate-to-clr-pure-cpp-cli.md)  
  
-   [进程](../cpp/process.md)  
  
## 请参阅  
 [混合（本机和托管）程序集](../dotnet/mixed-native-and-managed-assemblies.md)