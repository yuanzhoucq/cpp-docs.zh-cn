---
title: "OpenMP Libraries | Microsoft Docs"
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
ms.assetid: f89abf97-67e3-4327-bc30-43f85b9533a2
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OpenMP Libraries
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

讨论构成 Visual C\+\+ 的 OpenMP 运行库的 .lib 文件。  
  
 下面的库包含 Visual C\+\+ OpenMP 运行库函数。  
  
|OpenMP 运行库|特征|  
|----------------|--------|  
|VCOMP.LIB|多线程，动态链接 \(VCOMP.LIB 的导入库\)。|  
|VCOMPD.LIB|多线程，动态链接 \(VCOMPD.LID 的导入库\) \(调试\)|  
  
 如果 \_DEBUG 中定义，并且，如果 `#include omp.h` 在源代码中， VCOMPD.LIB 将默认为 LIB。  否则，将使用 VCOMP.LIB。  
  
 可以使用 [\/NODEFAULTLIB（忽略库）](../../../build/reference/nodefaultlib-ignore-libraries.md) 移除默认库和带有选定的 LIB 显式链接。  
  
 OpenMP DLL 在 Visual C\+\+ 可再发行组件目录并需要随使用 OpenMP 的应用程序。  
  
## 请参阅  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)