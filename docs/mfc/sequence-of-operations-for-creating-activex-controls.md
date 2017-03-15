---
title: "用于创建 ActiveX 控件的操作顺序 | Microsoft Docs"
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
  - "ActiveX 控件 [C++], 创建"
  - "MFC ActiveX 控件 [C++], 创建"
  - "OLE 控件 [C++], MFC"
  - "序列 [C++]"
  - "序列 [C++], 用于创建 ActiveX 控件"
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 用于创建 ActiveX 控件的操作顺序
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下表显示效果和框架的效果在创建 ActiveX 控件 \(以前称为 OLE 控件\)。  
  
### 创建ActiveX 控件  
  
|任务|You do|框架|  
|--------|------------|--------|  
|创建 ActiveX 控件框架。|运行 MFC ActiveX 控件向导创建控件。  指定可以在选项页需选项。  控件包含可选的类型和名称在项目，授权，subclassing 框和一个方法。|MFC ActiveX 控件向导"创建 ActiveX 控件的文件与基本功能，包括应用程序源文件、控件和属性页或页面；一个资源文件；一个项目文件；另，所有类型定制的规范。|  
|有关什么控件和 ActiveX 控件向导提供，而无需添加自己的代码行。|生成 ActiveX 控件和测试其与 Internet Explorer 或 [TSTCON 示例](../top/visual-cpp-samples.md)。|运行控件可以调整大小和移动。  它还可以调用的 **“关于”框** 方法 \(如果选择\)。|  
|实现控件方法和属性。|通过添加成员函数提供一公开的接口实现控件特定方法和属性来控制数据。  在确定时，添加成员变量存储数据结构并使用事件处理程序引发事件。|框架已定义映射的控件支持事件，属性和方法，使您侧重属性和方法如何执行。  默认属性页是可见的，并提供关于框的默认方法。|  
|构造控件的属性页或页。|使用 Visual C\+\+ 资源编辑器可视方式编辑控件属性页的接口：<br /><br /> -   创建其他的属性页。<br />-   创建并编辑位图、图标和光标。<br /><br /> 还可以测试在对话框编辑器的属性页。|MFC 应用程序向导"创建的默认资源文件提供所需的多个资源。  Visual C\+\+ 允许您编辑现有资源并轻松和视觉上添加新的资源。|  
|测试控件的事件、方法和属性。|重新生成控件并使用测试容器测试处理程序正常工作。|可以调用控件的方法，并通过属性页操作通过其属性连接或测试容器。  另外，使用测试容器为从控件接收通知和激发的径赛由控件的容器。|  
  
## 请参阅  
 [基于框架生成](../mfc/building-on-the-framework.md)   
 [用于生成 MFC 应用程序的操作顺序](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [用于创建 OLE 应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [用于创建数据库应用程序的操作顺序](../mfc/sequence-of-operations-for-creating-database-applications.md)