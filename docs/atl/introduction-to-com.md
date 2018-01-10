---
title: "COM 简介 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: 'index-page '
dev_langs: C++
helpviewer_keywords: COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2a8953949e722265afabc22410174b84c017276c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="introduction-to-com"></a>COM 简介
COM 是生成的 ActiveX 控件和 OLE 的基本"对象模型"。 COM 允许对象公开其功能的其他组件和主机应用程序。 它定义同时对象如何公开本身和跨进程和跨网络这种公开的工作原理。 COM 还定义对象的生命周期。  
  
 COM 的基础是这些概念：  
  
-   [接口](../atl/interfaces-atl.md)— 通过该对象公开其功能的机制。  
  
-   [IUnknown](../atl/iunknown.md) — 所有其他所基于的基本接口。 它实现的引用计数和查询机制运行通过 COM 接口  
  
-   [引用计数](../atl/reference-counting.md)-依据一个对象 （或严格地讲，一个接口） 决定当它不再使用，因此可以删除本身的技术。  
  
-   [QueryInterface](../atl/queryinterface.md) -用来查询给定的接口的对象的方法。  
  
-   [封送处理](../atl/marshaling.md)— 使对象能够跨线程、 进程和网络边界，从而使位置独立性使用的机制。  
  
-   [聚合](../atl/aggregation.md)— 一种方法，一个对象可以使用另一个。  
  
## <a name="see-also"></a>请参阅  
 [COM 和 ATL 简介](../atl/introduction-to-com-and-atl.md)   
 [组件对象模型](http://msdn.microsoft.com/library/windows/desktop/ms694363)

