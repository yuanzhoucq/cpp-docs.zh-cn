---
title: "资源文件 (C++) | Microsoft Docs"
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
  - "文件类型 [C++], 资源文件"
  - "资源文件"
  - "资源 [C++]"
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 资源文件 (C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

资源是向用户提供信息的界面元素。  位图、图标、工具栏和光标都是资源。  一些资源可以用来执行操作，例如从菜单中选择或在对话框中输入数据。  
  
 有关更多信息，请参见[使用资源](../mfc/working-with-resource-files.md)。  
  
|文件名|目录位置|解决方案资源管理器位置|说明|  
|---------|----------|-----------------|--------|  
|*Projname*.rc|*Projname*|源文件|项目的资源脚本文件。  资源脚本文件包含如下内容，具体取决于项目的类型和为项目选择的支持（例如工具栏、对话框或 HTML）：<br /><br /> -   默认菜单定义。<br />-   快捷键和字符串表。<br />-   默认**“关于”**对话框。<br />-   其他对话框。<br />-   图标文件 \(res\\*Projname*.ico\)。<br />-   版本信息。<br />-   位图。<br />-   工具栏。<br />-   HTML 文件。<br /><br /> 资源文件包含标准 Microsoft 基础类资源的文件 Afxres.rc。|  
|Resource.h|*Projname*|头文件|包含项目使用的资源定义的资源头文件。|  
|*Projname*.rc2|*Projname*\\res|源文件|包含项目使用的附加资源的脚本文件。  可以在项目的 .rc 文件的顶部包括 .rc2 文件。<br /><br /> .rc2 文件用于存放由多个不同项目使用的资源。  不必为不同的项目多次创建相同的资源，而是可以将它们放在一个 .rc2 文件中，然后将该 .rc2 文件包括在主 .rc 文件中。|  
|*Projname*.def|*Projname*|源文件|DLL 项目的模块定义文件。  对于控件，它提供控件的名称和说明以及运行时堆的大小。|  
|*Projname*.ico|*Projname*\\res|资源文件|项目或控件的图标文件。  该图标在应用程序最小化时出现。  它还用在应用程序的**“关于”**框中。  默认情况下，MFC 提供 MFC 图标，ATL 提供 ATL 图标。|  
|*Projname*Doc.ico|*Projname*\\res|资源文件|包括文档\/视图结构支持的 MFC 项目的图标文件。|  
|Toolbar.bmp|*Projname*\\res|资源文件|表示工具栏或调色板中的应用程序或控件的位图文件。  该位图包含在项目的资源文件中。  初始工具栏和状态栏在 **CMainFrame** 类中构造。|  
|ribbon.mfcribbon\-ms|*Projname*\\res|资源文件|资源文件，其中包含用于在功能区中定义按钮、控件和特性的 XML 代码。  有关更多信息，请参见[功能区设计器 \(MFC\)](../mfc/ribbon-designer-mfc.md)。|  
  
## 请参阅  
 [为 Visual C\+\+ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)