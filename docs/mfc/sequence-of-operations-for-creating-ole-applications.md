---
title: "用于创建 OLE 应用程序的操作顺序 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- OLE applications [MFC], creating
- OLE applications [MFC]
- applications [OLE], creating
- applications [OLE]
ms.assetid: 84b0f606-36c1-4253-9cea-44427f0074b9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: db3b5b9a5f4f62fa71cffa37b30a89aee41fe56f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="sequence-of-operations-for-creating-ole-applications"></a>用于创建 OLE 应用程序的操作顺序
下表显示你的角色和框架的角色中创建 OLE 链接和嵌入应用程序。 这些表示可用的选项而不是一个序列的步骤执行。  
  
### <a name="creating-ole-applications"></a>创建 OLE 应用程序  
  
|任务|您执行的操作|框架执行的操作|  
|----------|------------|------------------------|  
|创建 COM 组件。|运行 MFC 应用程序向导。 选择**完全服务器**或**袖珍服务器**中**复合文档支持**选项卡。|框架生成主干应用程序具有启用的 COM 组件功能。 所有 COM 功能可以传输到与仅稍加修改现有应用程序。|  
|从头开始创建容器应用程序。|运行 MFC 应用程序向导。 选择**容器**中**复合文档支持**选项卡。使用类视图，转到源代码编辑器。 填写 COM 处理程序函数的代码。|框架生成的主干应用程序可以插入由 COM 组件 （服务器） 应用程序创建的 COM 对象。|  
|创建从头支持自动化的应用程序。|运行 MFC 应用程序向导。 选择**自动化**从**高级功能**选项卡。使用类视图公开方法和自动化所需的应用程序中的属性。|框架生成的主干应用程序可以将其激活并自动执行其他应用程序。|  
  
## <a name="see-also"></a>请参阅  
 [基于框架生成](../mfc/building-on-the-framework.md)   
 [用于生成 MFC 应用程序的操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [用于创建 ActiveX 控件的操作顺序](../mfc/sequence-of-operations-for-creating-activex-controls.md)   
 [数据库应用程序的创建操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)

