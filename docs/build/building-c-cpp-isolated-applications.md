---
title: "生成 C/C++ 独立应用程序 | Microsoft Docs"
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
  - "独立的应用程序 [C++]"
ms.assetid: 8a2fe4fa-0489-433e-bfc6-495844d8d73a
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 生成 C/C++ 独立应用程序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

独立应用程序只依赖于并行程序集，且使用清单绑定到它的依赖项。  应用程序不必完全独立即可在 Windows 上正常运行；但是，使应用程序完全独立后，将来可以节省为应用程序提供服务的时间。  有关使应用程序完全独立的好处的更多信息，请参见[独立应用程序](http://msdn.microsoft.com/library/aa375190)。  
  
 在使用 Visual C\+\+ 生成本机 C\/C\+\+ 应用程序时，默认情况下，Visual Studio 项目系统将生成一个清单文件，用于描述应用程序在 Visual C\+\+ 库中的依赖项。  如果应用程序仅具有这些依赖项，则使用 Visual Studio 重新生成该应用程序时，它将变成独立应用程序。  如果应用程序在运行时还使用其他库，则可能需要将那些库重新生成为并行程序集。有关步骤，请参见 [生成 C\/C\+\+ 并行程序集](../build/building-c-cpp-side-by-side-assemblies.md)。  
  
## 请参阅  
 [独立应用程序和并行程序集的概念](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [生成 C\/C\+\+ 独立应用程序和并行程序集](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)