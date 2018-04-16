---
title: "添加 ATL OLE DB 使用者 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- ATL projects, adding ATL OLE DB consumers
- OLE DB, adding ATL OLE DB consumer to projects
- ATL OLE DB consumers
ms.assetid: f940a513-4e42-4148-b521-dd0d7dc89fa2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: defc933014bd287eb48f53635efba12a40960711
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="adding-an-atl-ole-db-consumer"></a>添加 ATL OLE DB 使用者
使用此向导以向项目添加 ATL OLE DB 使用者。 ATL OLE DB 使用者包含 OLE DB 访问器类和数据绑定访问数据源所必需。 为 ATL COM 应用程序，或作为 MFC 或 Win32 应用程序包含 ATL 支持 （其中 ATL OLE DB 使用者向导自动添加），该项目必须已创建。  
  
 **请注意**可以向 MFC 项目添加 OLE DB 使用者。 如果这样做，ATL OLE DB 使用者向导会将必要的 COM 支持添加到你的项目。 这假定在你创建 MFC 项目，你选择**ActiveX 控件**复选框 (在**高级功能**MFC 项目应用程序向导页)，这以默认方式检查。 选择此选项可确保在应用程序调用**CoInitialize**和**CoUninitialize**。 如果你未选择**ActiveX 控件**时创建 MFC 项目时，需要调用**CoInitialize**和**CoUninitialize**主代码中。  
  
### <a name="to-add-an-atl-ole-db-consumer-to-your-project"></a>若要添加到你的项目的 ATL OLE DB 使用者  
  
1.  在类视图中，右键单击该项目。 在快捷菜单上，单击**添加**，然后单击**添加类**。  
  
2.  在 Visual c + + 文件夹中，双击**ATL OLE DB 使用者**图标或选择它，然后单击**打开**。  
  
     ATL OLE DB 使用者向导将打开。  
  
3.  定义设置中所述[ATL OLE DB 使用者向导](../../atl/reference/atl-ole-db-consumer-wizard.md)。  
  
4.  单击**完成**关闭向导。 将在你的项目中插入新创建的 OLE DB 使用者代码。  
  
## <a name="see-also"></a>请参阅  
 [用代码向导添加功能](../../ide/adding-functionality-with-code-wizards-cpp.md)

