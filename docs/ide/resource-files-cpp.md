---
title: "资源文件 （c + +） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- resource files
- resources [C++]
- file types [C++], resource files
ms.assetid: 338a4a0f-0c62-4ef1-a34f-5d86262d93a4
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 097ae6d1486292d7dcc62dd4191e16f57e6f0a3c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="resource-files-c"></a>资源文件 (C++)
资源是向用户提供信息的界面元素。 位图、 图标、 工具栏和光标是所有资源。 一些资源可以操作以执行操作时，例如从菜单中选择或在对话框中输入的数据。  
  
 请参阅[处理资源](../windows/working-with-resource-files.md)有关详细信息。  
  
|文件名|目录位置|解决方案资源管理器位置|描述|  
|---------------|------------------------|--------------------------------|-----------------|  
|*Projname*.rc|*Projname*|源文件|项目的资源脚本文件。 资源脚本文件包含以下内容，具体取决于项目，然后选择项目 （例如，工具栏、 对话框框中，或 HTML） 的支持的类型：<br /><br /> 默认菜单定义。<br />-快捷键和字符串表。<br />-默认**有关**对话框。<br />-其他对话框。<br />图标文件 (res\\*Projname*.ico)。<br />版本信息。<br />-位图。<br />-工具栏。<br />HTML 文件。<br /><br /> 资源文件包含标准的 Microsoft 基础类资源的文件 Afxres.rc。|  
|Resource.h|*Projname*|头文件|资源标头文件，包括由项目使用的资源的定义。|  
|*Projname*.rc2|*Projname*\res|源文件|包含由项目使用的其他资源的脚本文件。 你可以包括在项目的.rc 文件顶部的.rc2 文件。<br /><br /> .Rc2 文件可用于包括几个不同项目使用的资源。 而不必创建不同项目的若干次相同的资源，你可以将它们放在.rc2 文件，并且到主.rc 文件包括.rc2 文件。|  
|*Projname*.def|*Projname*|源文件|DLL 项目的模块定义文件。 用于控件，它提供的名称和描述的控件，以及运行时堆的大小。|  
|*Projname*.ico|*Projname*\res|资源文件|用于项目或控件的图标文件。 应用程序最小化时，会显示此图标。 它还用在应用程序的**有关**框。 默认情况下，MFC 提供了 MFC 图标，和 ATL 提供 ATL 图标。|  
|*Projname*Doc.ico|*Projname*\res|资源文件|MFC 项目支持的文档/视图体系结构的图标文件。|  
|Toolbar.bmp|*Projname*\res|资源文件|表示应用程序或工具栏或调色板中的控件的位图文件。 该位图包含项目的资源文件中。 在中构造的初始工具栏和状态栏**CMainFrame**类。|  
|ribbon.mfcribbon ms|*Projname*\res|资源文件|包含用于定义功能区中的按钮、 控件和特性的 XML 代码的资源文件。 有关详细信息，请参阅 [Ribbon Designer (MFC)](../mfc/ribbon-designer-mfc.md)。|  
  
## <a name="see-also"></a>请参阅  
 [为 Visual C++ 项目创建的文件类型](../ide/file-types-created-for-visual-cpp-projects.md)