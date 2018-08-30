---
title: COM 简介 |Microsoft Docs
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
ms.openlocfilehash: 5a408ecb1a96aab284a4ac8c7cdd59909ed7c0ea
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216518"
---
# <a name="introduction-to-com"></a>COM 简介
COM 上的 ActiveX 控件和 OLE 生成的是基本"对象模型"。 COM 允许对象向其他组件和主机应用程序公开其功能。 它定义了对象如何公开本身和跨进程和跨网络这种公开的工作原理。 COM 还定义了对象的生命周期。  
  
 COM 的基础是这些概念：  
  
-   [接口](../atl/interfaces-atl.md)— 通过该对象公开其功能的机制。  
  
-   [IUnknown](../atl/iunknown.md) — 所有其他人所基于的基本接口。 它实现引用计数和查询机制的运行通过 COM 接口  
  
-   [引用计数](../atl/reference-counting.md)— 依据对象 （或严格地讲，一个接口） 决定当它不再使用，因此删除自身的技术。  
  
-   [QueryInterface](../atl/queryinterface.md) -用来查询给定接口的对象的方法。  
  
-   [封送处理](../atl/marshaling.md)— 使对象能够跨线程、 进程和网络边界，从而使位置独立性使用的机制。  
  
-   [聚合](../atl/aggregation.md)— 一种方法，一个对象可使用另一个。  
  
## <a name="see-also"></a>请参阅  
 [COM 和 ATL 简介](../atl/introduction-to-com-and-atl.md)   
 [组件对象模型](/windows/desktop/com/the-component-object-model)

