---
title: "COM + 1.0 支持在 ATL 项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.appwiz.ATL.MTS
dev_langs: C++
helpviewer_keywords: ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 33b93084a99154aea671c877aae7d80e48485202
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/24/2017
---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 支持在 ATL 项目
你可以使用[ATL 项目向导](../../atl/reference/creating-an-atl-project.md)以创建项目对 COM + 1.0 组件的基本支持。  
  
 COM + 1.0 旨在用于开发的基于组件的分布式应用程序。 它还提供用于部署和管理这些应用程序的运行时基础结构。  
  
 如果你选择**支持 COM + 1.0**复选框，向导将修改在链接步骤的生成脚本。 具体而言，COM + 1.0 项目链接到以下库：  
  
-   comsvcs.lib  
  
-   Mtxguid.lib  
  
 如果你选择**支持 COM + 1.0**复选框，你还可以选择**支持组件注册机构**。 组件注册机构允许你 COM + 1.0 对象获取组件的列表、 注册组件，或注销组件 （单独或在一次）。  
  
## <a name="see-also"></a>另请参阅  
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [使用 ATL 和 C 运行时代码编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

