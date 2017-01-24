---
title: "从类型库添加 MFC 类 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "类 [C++], 添加 MFC"
  - "MFC, 从类型库添加类"
  - "类型库, 添加 MFC 类自"
ms.assetid: aba40476-3cfb-47af-990e-ae2e9e0d79cf
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 从类型库添加 MFC 类
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用该向导从可用类型库中的接口创建 MFC 类。  可以向 [MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)、[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md) 或 [MFC ActiveX 控件](../../mfc/reference/creating-an-mfc-activex-control.md)中添加 MFC 类。  
  
> [!NOTE]
>  不需要创建启用自动化的 MFC 项目，也可以从类型库添加类。  
  
 类型库包含组件公开的接口的二进制说明，定义了方法及其参数和返回类型。  必须注册类型库，它才会显示在“从类型库添加类向导”中的“可用类型库”列表中。  有关更多信息，请参见 MSDN Library 中的“分布式 COM 的内部：类型库和语言集成”。  
  
### 从类型库添加 MFC 类  
  
1.  在**解决方案资源管理器**或[“类视图”](http://msdn.microsoft.com/zh-cn/8d7430a9-3e33-454c-a9e1-a85e3d2db925)中，右击要向其添加类的项目名称。  
  
2.  从快捷菜单中单击“添加”，然后单击“添加类”。  
  
3.  在[添加类](../../ide/add-class-dialog-box.md)对话框中，在“模板”窗格中，单击“类型库中的 MFC 类”，然后单击“打开”显示[从类型库添加类向导](../../mfc/reference/add-class-from-typelib-wizard.md)。  
  
 在该向导中，可以添加类型库中的多个类。  同样，在单个向导会话中可以从多个类型库添加类。  
  
 该向导为从选定的类型库添加的每个接口创建 MFC 类（派生自 [COleDispatchDriver](../../mfc/reference/coledispatchdriver-class.md)）。  `COleDispatchDriver` 实现 OLE 自动化的客户端。  
  
## 请参阅  
 [自动化客户端](../../mfc/automation-clients.md)   
 [自动化客户端：使用类型库](../../mfc/automation-clients-using-type-libraries.md)