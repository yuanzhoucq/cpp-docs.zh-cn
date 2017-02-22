---
title: "指定项目的线程模型 (ATL) | Microsoft Docs"
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
  - "_ATL_APARTMENT_THREADED 宏"
  - "_ATL_FREE_THREADED 宏"
  - "_ATL_SINGLE_THREADED 宏"
  - "ATL, 多线程处理"
  - "线程处理 [ATL], 模型"
ms.assetid: 6b571078-521c-4f3e-9f08-482aa235a822
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 指定项目的线程模型 (ATL)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下面的宏可指定ATL项目的线程处理模型:  
  
|宏|使用准则|  
|-------|----------|  
|\_ATL\_SINGLE\_THREADED|所有条件，则您的对象使用单个线程模型，请定义。|  
|\_ATL\_APARTMENT\_THREADED|如果一个或多个对象所使用单元线程处理，请定义。|  
|\_ATL\_FREE\_THREADED|如果一个或多个对象所使用释放或非特定线程处理，请定义。  现有代码可以包含对等效的宏 [\_ATL\_MULTI\_THREADED](../Topic/_ATL_MULTI_THREADED.md)。|  
  
 如果不定义项目的这些宏中的任何一，\_ATL\_FREE\_THREADED将生效。  
  
 宏影响运行时性能如下所示:  
  
-   指定一个对应于项目的对象的宏可以提高运行时性能。  
  
-   指定更高的宏，例如，如果指定\_ATL\_APARTMENT\_THREADED，当您的所有对象是单线程，将稍微降低运行时性能。  
  
-   指定宏底部，例如，因此，如果指定\_ATL\_SINGLE\_THREADED，在一个或多个对象所使用单元线程或"自由线程处理时，可能会导致应用程序在运行时失败。  
  
 为线程模型的说明参见 [选项，ATL简单对象向导](../atl/reference/options-atl-simple-object-wizard.md) 可用于ATL对象。  
  
## 请参阅  
 [概念](../atl/active-template-library-atl-concepts.md)