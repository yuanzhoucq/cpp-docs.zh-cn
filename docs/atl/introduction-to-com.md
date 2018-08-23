---
title: COM 简介 |Microsoft 文档
ms.custom: index-page
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- COM
ms.assetid: 120735d9-db71-4ad3-a730-ce576ea2354e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 938d0c45cae5ec9a2988f77f539af1a3d5513b83
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
ms.locfileid: "32356170"
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

