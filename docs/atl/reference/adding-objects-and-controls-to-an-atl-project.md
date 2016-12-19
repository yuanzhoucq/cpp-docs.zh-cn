---
title: "向 ATL 项目添加对象和控件 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.appwiz.ATL.controls"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 控件向导"
  - "ATL 项目, 添加控件"
  - "ATL 项目, 添加对象"
  - "控件 [ATL], 添加到项目"
  - "对象 [C++], 添加到 ATL 项目"
  - "向导 [C++], ATL 项目"
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 向 ATL 项目添加对象和控件
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以使用某个 ATL 代码向导将对象或者控件添加到基于 ATL 或 MFC 的项目。  对于添加的每个 COM 对象或者控件，向导生成 .cpp 和 .h 文件，以及用于基于脚本的注册表支持的 .rgs 文件。  Visual Studio 中有下列可用的 ATL 代码向导：  
  
||||  
|-|-|-|  
|[ATL 简单对象](../../atl/reference/atl-simple-object-wizard.md)|[ATL 对话框](../../atl/reference/atl-dialog-wizard.md)|[ATL 控件](../../atl/reference/atl-control-wizard.md)|  
|[ATL 属性页](../../atl/reference/atl-property-page-wizard.md)|[ATL Active Server Page 组件](../../atl/reference/atl-active-server-page-component-wizard.md)|[ATL OLE DB 使用者](../../atl/reference/atl-ole-db-consumer-wizard.md)|  
|[向 MFC 添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[ATL COM\+ 1.0 组件向导](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[ATL OLE DB 提供程序](../../atl/reference/atl-ole-db-provider-wizard.md)|  
  
> [!NOTE]
>  在向项目中添加 ATL 对象前，应该在对象的相关帮助主题中查看它的详细信息和要求。  
  
### 使用 ATL 控件向导添加对象或者控件  
  
1.  在“解决方案资源管理器”中，右击项目节点并在快捷菜单上单击“添加”。  单击“添加类”。  
  
     即会出现[“添加类”](../../ide/add-class-dialog-box.md)对话框。  
  
2.  利用在“类别”窗格中选定的 ATL 文件夹，从“模板”窗格中选择要插入的对象。  单击**“打开”**。  出现选定对象的代码向导。  
  
    > [!NOTE]
    >  如果要向 MFC 项目中添加 ATL 对象，必须先为现有的项目添加 ATL 支持。  可以遵循[向 MFC 项目添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)中的说明来完成此操作。  
  
     或者，如果尝试在不事先添加 ATL 支持的情况下向 MFC 项目添加 ATL 对象，Visual Studio 将提示您指定是否希望为项目添加 ATL 支持。  单击**“是”**为项目添加 ATL 支持并打开选定的 ATL 向导。  
  
## 请参阅  
 [ATL 项目向导](../../atl/reference/atl-project-wizard.md)   
 [Visual C\+\+ 项目类型](../../ide/visual-cpp-project-types.md)   
 [使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)   
 [Fundamentals of ATL COM Objects](../../atl/fundamentals-of-atl-com-objects.md)   
 [使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)   
 [默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)