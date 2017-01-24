---
title: "附加启动注意事项 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "main 之前初始化"
  - "程序启动 [C++]"
  - "启动代码"
ms.assetid: 0e942aa6-8342-447c-b068-8980ed7622bd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 附加启动注意事项
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在 C\+\+ 中，对象构造和析构可能涉及执行用户代码。  因此，了解进入 **main** 前发生的初始化和退出 **main** 后调用的析构函数很重要的。（有关构造函数和析构函数的详细信息，请参阅[构造函数](../cpp/constructors-cpp.md)和[析构函数](../cpp/destructors-cpp.md)。）  
  
 进入 **main** 前将发生以下初始化：  
  
-   静态数据默认初始化为零。  没有显式初始值设定项的所有静态数据在执行任何其他代码（包括运行时初始化）前设置为零。  静态数据成员仍必须显式定义。  
  
-   翻译单元中的全局静态对象的初始化。  这可能在进入 **main** 前或初次使用全局静态对象的翻译单元中的任何函数或对象前发生。  
  
 **Microsoft 专用**  
  
 在 Microsoft C\+\+ 中，全局静态对象在进入 **main** 前进行初始化。  
  
 **结束 Microsoft 专用**  
  
 相互依赖但位于不同翻译单元中的全局静态对象会导致错误行为。  
  
## 请参阅  
 [启动和终止](../cpp/startup-and-termination-cpp.md)