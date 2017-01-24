---
title: "多线程库性能 | Microsoft Docs"
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
  - "库, 多线程"
  - "多线程库"
  - "性能, 多线程处理"
  - "线程处理 [C++], 性能"
ms.assetid: faa5d808-087c-463d-8f0d-8c478d137296
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多线程库性能
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

单线程的 CRT 不再可用。  本主题讨论如何从多线程库获取最佳性能。  
  
## 极大优化性能  
 提高了多线程 \(msvcrt.lib\) 库的性能并接近将消除的单线程库的性能。  当需要高性能时，对于这些情况，有多种新功能。  
  
-   独立流锁可以锁定流然后直接使用流访问的 [\_nolock 函数](../c-runtime-library/nolock-functions.md)。  这允许锁定用法是关键的外部循环。  
  
-   每线程区域设置减少多线程方案的区域设置访问的开销 \(参见 [\_configthreadlocale](../c-runtime-library/reference/configthreadlocale.md)\)。  
  
-   区域设置相关的函数名称 \(其中以\_l结尾\) 将区域设置作为一个参数，移除严格的成本 \(例如，[printf、\_printf\_l、wprintf、\_wprintf\_l](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)\)。  
  
-   公共代码的优化降低许多表短的操作的开销。  
  
-   [\_CRT\_DISABLE\_PERFCRIT\_LOCKS](../c-runtime-library/crt-disable-perfcrit-locks.md) 定义强制所有 I\/O 操作均采用单线程的模型使用 I\/O 和函数的\_nolock 窗体。  这允许高度基于 I\/O 的单一线程的应用程序将获得更好的性能。  
  
-   CRT 堆句柄的公开用于启用 CRT 堆窗口右下角堆碎片 \(LFH\)，可以充分地提高在高度缩放方案的性能。  
  
## 请参阅  
 [CRT 库功能](../c-runtime-library/crt-library-features.md)