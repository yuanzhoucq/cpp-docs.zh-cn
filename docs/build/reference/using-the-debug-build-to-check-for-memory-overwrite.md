---
title: "使用调试版本检查内存改写 | Microsoft Docs"
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
  - "内存, 改写"
ms.assetid: 1345eb4d-24ba-4595-b1cc-2da66986311e
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 使用调试版本检查内存改写
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要使用调试版本检查内存覆盖，首先必须重新生成用于调试的项目。  然后，转到应用程序的 `InitInstance` 函数的开始处并添加下行：  
  
```  
afxMemDF |= checkAlwaysMemDF;  
```  
  
 调试内存分配器在所有内存分配的周围都放置保护字节。  然而，除非检查这些保护字节是否已被更改（这将指示内存覆盖），否则它们没有什么用。  在其他方面，它们只是提供一个实际上可能使您得以逃避内存覆盖的缓冲区。  
  
 通过打开 `checkAlwaysMemDF`，每次调用 **new** 或 **delete** 时都会强制 MFC 调用 `AfxCheckMemory` 函数。  如果检测到内存覆盖，它会生成一个类似于下面这样的 TRACE 消息：  
  
```  
Damage Occurred! Block=0x5533  
```  
  
 如果看到这些消息之一，需要逐句通过代码以确定发生损坏的位置。  为了更精确地找出发生内存覆盖的位置，您可以亲自显式调用 `AfxCheckMemory`。  例如：  
  
```  
ASSERT(AfxCheckMemory());  
    DoABunchOfStuff();  
    ASSERT(AfxCheckMemory());  
```  
  
 如果第一个 ASSERT 成功而第二个失败，这表示内存覆盖一定发生在这两次调用之间的函数中。  
  
 根据应用程序的性质，您可能发现 `afxMemDF` 导致程序运行得太慢，以至甚至无法进行测试。  每次调用 new 和 delete 时，`afxMemDF` 变量都导致 `AfxCheckMemory` 被调用。  对于这种情况，应按以上显示的那样分散您自己对 `AfxCheckMemory`\( \) 的调用，并尝试以此方法找出内存覆盖。  
  
## 请参阅  
 [修复发行版本问题](../../build/reference/fixing-release-build-problems.md)