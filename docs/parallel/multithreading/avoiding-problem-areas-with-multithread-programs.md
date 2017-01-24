---
title: "避免与多线程程序有关的问题 | Microsoft Docs"
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
  - "错误 [C++], 多线程程序"
  - "多线程处理 [C++], 疑难解答"
  - "线程处理 [C++], 疑难解答"
  - "疑难解答 [C++], 多线程处理"
ms.assetid: 06cc231d-bb5a-409d-8bd3-676c9e2a8c5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 避免与多线程程序有关的问题
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在创建、链接或执行多线程 C 程序时可能会遇到几种问题。  下表将对一些更常见的问题进行描述。（有关从 MFC 角度进行的类似讨论，请参见[多线程编程：编程提示](../../parallel/multithreading-programming-tips.md)。）  
  
|问题|可能的原因|  
|--------|-----------|  
|出现一个消息框，显示程序已导致保护冲突。|许多 Win32 编程错误导致保护冲突。  导致保护冲突的常见原因是间接将数据分配给 null 指针。  因为这会导致程序尝试访问不属于它的内存，所以发出保护冲突。<br /><br /> 检测导致保护冲突原因的一个很容易的方式就是使用调试信息编译程序，然后在 Visual C\+\+ 环境中通过调试器运行程序。  发生保护错误时，Windows 将控制传输到调试器，光标会定位在导致问题的行上。|  
|程序生成许多编译和链接错误。|通过将编译器的警告等级设置为最高值之一并注意警告消息，可以消除许多潜在问题。  通过使用等级为 3 或等级为 4 的警告等级选项，可以检测意外的数据转换、丢失的函数原型和非 ANSI 功能的使用。|  
  
## 请参阅  
 [使用 C 和 Win32 进行多线程编程](../../parallel/multithreading-with-c-and-win32.md)