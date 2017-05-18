---
title: "COM + 1.0 支持在 ATL 项目 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- vc.appwiz.ATL.MTS
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, COM+ 1.0 support
ms.assetid: 51fb08ac-d632-4657-a4e0-d3f989f0b6f8
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 7521c1dae6fd29b8b951d23fe33c91179d4b46ed
ms.contentlocale: zh-cn
ms.lasthandoff: 02/24/2017

---
# <a name="com-10-support-in-atl-projects"></a>COM + 1.0 支持在 ATL 项目
您可以使用[ATL 项目向导](../../atl/reference/creating-an-atl-project.md)若要创建一个项目对 COM + 1.0 组件的基本支持。  
  
 COM + 1.0 专为开发基于组件的分布式应用程序。 它还提供用于部署和管理这些应用程序的运行时基础结构。  
  
 如果您选择**支持 COM + 1.0**复选框后，向导将修改链接步骤中的生成脚本。 具体而言，COM + 1.0 项目链接到以下库︰  
  
-   comsvcs.lib  
  
-   Mtxguid.lib  
  
 如果您选择**支持 COM + 1.0**复选框，您还可以选择**支持组件注册器**。 组件注册器使您的 COM + 1.0 对象，若要获取的组件的列表、 注册组件，或注销组件 （单独或一次性）。  
  
## <a name="see-also"></a>另请参阅  
 [ATL COM 对象的基础知识](../../atl/fundamentals-of-atl-com-objects.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)


