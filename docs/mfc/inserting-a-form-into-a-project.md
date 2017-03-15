---
title: "在项目中插入窗体 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "窗体, 添加到项目"
  - "“新插入”对话框"
  - "插入窗体"
ms.assetid: f3bd2998-3ce2-496d-ac5c-57ca70eec7cb
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# 在项目中插入窗体
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

窗体控件为提供方便容器。  应用程序，只要支持 MFC 库，可以轻松地将一个窗体分成基于 MFC 的应用程序。  
  
### 插入窗体到项目  
  
1.  从类视图中，选中要添加窗体的项目，再单击鼠标右键。  
  
2.  从快捷菜单中单击“添加”，然后单击“添加类”。  
  
     **New Form** 如果命令不可用，项目可能基于活动模板库 \(ATL\) \(ATL\)。  当第一次创建项目，若要将该窗体添加到 ATL 项目，您必须。[指定一些设置](../atl/reference/application-settings-atl-project-wizard.md)  
  
3.  在 **MFC\(M\)** 文件夹，单击 **MFC 类**。  
  
4.  使用 MFC 类向导，请将新类从派生。[CFormView](../mfc/reference/cformview-class.md)  
  
 Visual C\+\+ 将该窗体添加到应用程序中，它在对话框编辑器内打开，以便可以开始添加控件并在其工作的总体设计。  
  
 可能需要执行以下附加步骤 \(适用于为基于对话框的应用程序\):  
  
1.  重写 `OnUpdate` 成员函数。  
  
2.  实现的成员函数将视图的数据移动到文档。  
  
3.  创建 `OnPrint` 成员函数。  
  
## 请参阅  
 [窗体视图](../mfc/form-views-mfc.md)