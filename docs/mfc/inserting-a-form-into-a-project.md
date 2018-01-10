---
title: "一个项目中插入窗体 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- inserting forms [MFC]
- Insert New dialog box [MFC]
- forms, adding to projects
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 968c24a4f64b88be6de95f0f1dd98c09eb494a97
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="inserting-a-form-into-a-project"></a>在项目中插入窗体
窗体为控件提供一个方便的容器。 只要应用程序支持的 MFC 库，你可以轻松插入到你的应用程序的基于 MFC 的窗体。  
  
### <a name="to-insert-a-form-into-your-project"></a>若要向项目中插入窗体  
  
1.  从类视图中，选择你想要添加该窗体，的项目并单击鼠标右键按钮。  
  
2.  从快捷菜单中，单击**添加**，然后单击**添加类**。  
  
     如果**新窗体**命令不可用，你的项目可能基于活动模板库 (ATL)。 若要向 ATL 项目添加窗体，你必须[指定某些设置](../atl/reference/application-settings-atl-project-wizard.md)首次创建项目时。  
  
3.  从**MFC**文件夹中，单击**MFC 类**。  
  
4.  使用 MFC 类向导，使新类派生自[CFormView](../mfc/reference/cformview-class.md)。  
  
 Visual c + + 将窗体添加到你的应用程序，打开在对话框编辑器，以便你可以开始添加控件和处理其总体设计。  
  
 你可能想要执行以下附加步骤 （不适用于基于对话框的应用程序）：  
  
1.  重写`OnUpdate`成员函数。  
  
2.  实现的成员函数将从你的视图的数据移到文档。  
  
3.  创建`OnPrint`成员函数。  
  
## <a name="see-also"></a>请参阅  
 [窗体视图](../mfc/form-views-mfc.md)

