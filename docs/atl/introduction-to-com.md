---
title: "COM 介绍 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "index-page "
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM"
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
caps.latest.revision: 11
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# COM 介绍
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

COM一直是“对象模型”在其中ActiveX控件和OLE生成。  COM允许对象将它的功能向其他组件和主机应用程序。  它定义对象的方式显示自身，并且此风险的工作方式在网络处理和。  COM还定义对象的生命周期。  
  
 对COM的基础是这些概念:  
  
-   [接口](../atl/interfaces-atl.md) —对象公开其功能的结构。  
  
-   [IUnknown](../atl/iunknown.md) —其他的基本接口。  它实现查询结构的引用计数和接口运行通过COM。  
  
-   [reference计数](../atl/reference-counting.md) —对象的方法\(或，强，接口\)因此不再决定何时使用和是可用移除它。  
  
-   [QI](../atl/queryinterface.md) —使用的方法查询特定接口的对象。  
  
-   [线](../atl/marshaling.md) —使对象在线程中使用的结构，处理和网络边界，允许位置无关。  
  
-   [摘要](../atl/aggregation.md) —一种在哪个对象可以利用个。  
  
## 请参阅  
 [Introduction to COM and ATL](../atl/introduction-to-com-and-atl.md)   
 [The Component Object Model](http://msdn.microsoft.com/library/windows/desktop/ms694363)