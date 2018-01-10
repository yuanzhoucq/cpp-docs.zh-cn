---
title: "实现连接点向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.codewiz.impl.cp.overview
dev_langs: C++
helpviewer_keywords: Implement Connection Point Wizard [C++]
ms.assetid: c117f6c6-30f0-4adb-82b4-b1f34e0f0fa8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f29b4f25d937c2f538373ff85819f7315150e712
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="implement-connection-point-wizard"></a>实现连接点向导
此向导实现 COM 对象的连接点。 可连接对象 （即，对源） 可以公开连接点为其自身接口或任何传出的接口。 Visual c + + 和 Windows 都提供有输出接口的类型库。 每个输出接口可以实现客户端上的对象 （即，接收器）。  
  
 有关详细信息，请参阅[ATL 连接点](../atl/atl-connection-points.md)。  
  
 **可用的类型库**  
 显示包含可以实现连接点的接口定义的可用类型库。 单击省略号按钮以找到包含要使用的类型库的文件。  
  
 **位置**  
 显示的类型库中当前选定位置**可用的类型库**列表。  
  
 **接口**  
 显示其定义中当前选定的类型库中包含的接口**可用的类型库**框。  
  
|传输按钮|描述|  
|---------------------|-----------------|  
|**>**|将添加到**实现连接点**列表中当前选定的接口名称**接口**列表。|  
|**>>**|将添加到**实现连接点**列表中可用的所有接口名称**接口**都列表。|  
|**<**|移除中当前选定的接口名称**实现连接点**列表。|  
|**<<**|删除的所有接口名称中当前列出**实现连接点**列表。|  
  
 **实现连接点**  
 显示当你单击时实现连接点的接口名称**完成**。  
  
## <a name="see-also"></a>请参阅  
 [实现连接点](../ide/implementing-a-connection-point-visual-cpp.md)