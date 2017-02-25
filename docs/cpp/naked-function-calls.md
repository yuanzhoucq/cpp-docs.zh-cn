---
title: "Naked 函数调用 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "epilog 代码"
  - "naked 函数"
  - "naked 关键字 [C++]"
  - "naked 关键字 [C++], storage-class 特性"
  - "prolog 代码"
  - "虚拟设备驱动程序"
  - "虚拟设备驱动程序, naked 函数调用"
  - "VXD 虚拟设备驱动程序"
ms.assetid: 2a66847a-a43f-4541-a7be-c9f5f29b5fdb
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Naked 函数调用
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Microsoft 专用  
 无需 prolog 或 epilog 代码即可发出使用 `naked` 特性声明的函数，这使您能够使用[内联汇编程序](../assembler/inline/inline-assembler.md)编写您自己的自定义 prolog\/epilog 序列。  将裸函数作为高级功能提供。  利用这些函数，您可以声明从 C\/C\+\+ 之外的上下文中调用的函数，从而作出有关参数位置或保留哪些寄存器的各种假设。  示例包括例程（如中断处理程序）。  此功能对于虚拟设备驱动程序 \(VxDs\) 的编写器特别有用。  
  
## 您想进一步了解什么？  
  
-   [naked](../cpp/naked-cpp.md)  
  
-   [裸函数的规则和限制](../cpp/rules-and-limitations-for-naked-functions.md)  
  
-   [有关编写 Prolog\/Epilog 代码的注意事项](../cpp/considerations-for-writing-prolog-epilog-code.md)  
  
### 结束 Microsoft 专用  
  
## 请参阅  
 [调用约定](../cpp/calling-conventions.md)