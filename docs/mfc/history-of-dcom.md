---
title: "DCOM 历史记录 | Microsoft Docs"
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
  - "DCOM"
  - "DCOM, 关于 DCOM"
  - "远程自动化, DCOM"
ms.assetid: c21aa0ea-1396-4b52-b77f-88fb0fdd2a5c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DCOM 历史记录
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当自动在 1993 年首次引入的，则只能使用。在同一台计算机上运行的应用程序。  但是，共享，因为，也就是说，它支柱和 OLE 的相同 COM \(或组件对象模型 \(COM\)\)，始终要将变为“远程处理”，当 COM 更新为包括远程处理功能。  还计划从纯粹本地操作过渡到分布的操作需要对现有代码的很少或未更改。  
  
 因此哪些“远程处理表示”?  本地 COM 声明接口的使用者计算机上驻留并执行该接口与提供程序。  例如，Microsoft Visual Basic 可控制 Microsoft Excel 复制桌面上计算机上，的执行，但不能处理 Excel 在另一台计算机上。  分布式 COM 的开发，接口的使用者不需要在计算机和接口提供程序执行的相同。  
  
 COM 后调整网络的工作，然后未附加到本地执行模型 \(所有接口有些接口对本地计算机的内部结构的关系，例如方法让处理到设备上下文作为参数\) 会分发功能的这些接口绘制。  接口将使用者发出一个需要特定接口；该接口无法目标操作的实例提供 \(或将运行\) 在不同的计算机上。  在 COM 中分配机制。通信使用者到提供程序，在这种情况下使用者发出的方法调用会在提供程序结束，则会执行。  所有返回值随后会发送给使用者。  实际上，发布操作是透明的使用者和提供程序。  
  
 这样各种 COM 当前存在。  DCOM \(用于“分布式 COM”\) 附带的版本从 Windows NT 4.0 版和包括 Windows 2000 开始。  由于 1996 年末，它还为 Windows 9x 可用。  在这两种情况下，组件包括一组替换和其他的 DLL，使用这些实用工具，提供本地和远程 COM 的功能。  因此现在是基于 Win32 平台的一个内部的一部分并且随可在其他平台。其他组织。  
  
## 本节内容  
 [远程的自动化以位置？](../mfc/where-does-remote-automation-fit-in-q.md)  
  
 [远程的自动化提供什么？](../mfc/what-does-remote-automation-provide-q.md)  
  
## 请参阅  
 [远程自动化](../mfc/remote-automation.md)