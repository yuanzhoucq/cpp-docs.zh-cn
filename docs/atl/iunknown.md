---
title: "IUnknown | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IUnknown"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "COM 接口, base interface"
  - "IUnknown interface"
ms.assetid: e6b85472-e54b-4b8c-b19f-4454d6c05a8f
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IUnknown
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509) 是其他任何 COM 接口的基接口。此接口可定义三种方法：[QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521)、[AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317)。  [QueryInterface](http://msdn.microsoft.com/library/windows/desktop/ms682521) 允许界面用户向对象要求另一个界面的指针。  [AddRef](http://msdn.microsoft.com/library/windows/desktop/ms691379) 和 [Release](http://msdn.microsoft.com/library/windows/desktop/ms682317) 在接口上实现引用计数。  
  
## 请参阅  
 [COM 介绍](../atl/introduction-to-com.md)   
 [IUnknown and Interface Inheritance](http://msdn.microsoft.com/library/windows/desktop/ms692713)