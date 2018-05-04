---
title: COM + 1.0 支持在 ATL 项目 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e3440d3ed2e3244b35588d5c07fd181f1ad2f082
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 支持在 ATL 项目
你可以使用[ATL 项目向导](../../atl/reference/creating-an-atl-project.md)以创建项目对 COM + 1.0 组件的基本支持。  
  
 COM + 1.0 旨在用于开发的基于组件的分布式应用程序。 它还提供用于部署和管理这些应用程序的运行时基础结构。  
  
 如果你选择**支持 COM + 1.0**复选框，向导将修改在链接步骤的生成脚本。 具体而言，COM + 1.0 项目链接到以下库：  
  
-   comsvcs.lib  
  
-   Mtxguid.lib  
  
 如果你选择**支持 COM + 1.0**复选框，你还可以选择**支持组件注册机构**。 组件注册机构允许你 COM + 1.0 对象获取组件的列表、 注册组件，或注销组件 （单独或在一次）。  
  
## <a name="see-also"></a>请参阅  
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [使用 ATL 和 C 运行时代码编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)

