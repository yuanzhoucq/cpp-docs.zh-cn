---
title: "MFC 应用程序向导 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.exe.overview
dev_langs:
- C++
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9d4997d2d793102119e5021ba1110db2674e1b42
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-application-wizard"></a>MFC 应用程序向导
MFC 应用程序向导生成应用程序，在编译时实现 Windows 可执行文件 (.exe) 应用程序的基本功能。 MFC 初学者应用程序包括 c + + 源文件 (.cpp)、 资源 (.rc) 文件、 标头 (.h) 文件和项目 (.vcxproj) 文件。 在这些初学者文件中生成的代码基于 MFC。  
  
> [!NOTE]
>  根据你选择的选项，该向导在你的项目中创建其他文件。 例如，如果你选择**上下文相关帮助**上[高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)页上，向导将创建编译项目的帮助文件所必需的文件。 有关此向导将创建的文件的详细信息，请参阅[Visual c + + 项目创建的文件类型](../../ide/file-types-created-for-visual-cpp-projects.md)，并查看项目中的 Readme.txt 文件。  
  
## <a name="overview"></a>概述  
 此向导页描述你创建的 MFC 应用程序的当前应用程序设置。 默认情况下，该向导创建项目，如下所示：  
  
-   [MFC 应用程序向导的应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)  
  
    -   使用选项卡式的多文档界面 (MDI) 支持创建项目。 有关详细信息，请参阅[SDI 和 MDI](../../mfc/sdi-and-mdi.md)。  
  
    -   项目使用[文档/视图体系结构](../../mfc/document-view-architecture.md)。  
  
    -   项目使用 Unicode 库。  
  
    -   项目使用 Visual Studio 项目样式创建的并启用视觉样式切换。  
  
    -   项目在共享 DLL 中使用 MFC。 有关详细信息，请参阅 [Visual C++ 中的 DLL](../../build/dlls-in-visual-cpp.md)。  
  
-   [MFC 应用程序向导的复合文档支持](../../mfc/reference/compound-document-support-mfc-application-wizard.md)  
  
    -   该项目的复合文档提供了不支持。  
  
-   [MFC 应用程序向导的文档模板字符串](../../mfc/reference/document-template-strings-mfc-application-wizard.md)  
  
    -   项目使用默认文档模板字符串的项目名称。  
  
-   [MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)  
  
    -   项目不提供支持的数据库。  
  
-   [MFC 应用程序向导的用户界面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)  
  
    -   项目实现标准的 Windows 用户界面功能，如系统菜单、 状态栏、 最大化和最大程度减少框中，**有关**框、 标准菜单栏和停靠工具栏和子框架。  
  
-   [MFC 应用程序向导的高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)  
  
    -   项目支持打印和打印预览。  
  
    -   项目支持 ActiveX 控件。 有关详细信息，请参阅[序列的操作用于创建 ActiveX 控件](../../mfc/sequence-of-operations-for-creating-activex-controls.md)。  
  
    -   该项目提供了不支持[自动化](../../mfc/automation.md)， [MAPI](../../mfc/mapi-support-in-mfc.md)， [Windows 套接字](../../mfc/windows-sockets-in-mfc.md)，或活动辅助功能。  
  
    -   项目支持**资源管理器**停靠的窗格中，**输出**停靠的窗格中，和一个**属性**停靠窗格。  
  
-   [MFC 应用程序向导的生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)  
  
    -   项目的视图类派生自[CView 类](../../mfc/reference/cview-class.md)。  
  
    -   项目的应用程序类派生自[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)。  
  
    -   项目的文档类派生自[CDocument 类](../../mfc/reference/cdocument-class.md)。  
  
    -   项目的主框架类派生自[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)。  
  
    -   项目的子框架类派生自[CMDIChildWndEx 类](../../mfc/reference/cmdichildwndex-class.md)。  
  
 若要更改这些默认设置，请单击向导左列中的相应的选项卡标题和显示的页，进行更改。  
  
 创建 MFC 应用程序项目后，可以将对象或控件添加到你的项目使用 Visual c + +[代码向导](../../ide/adding-functionality-with-code-wizards-cpp.md)。  
  
## <a name="see-also"></a>请参阅  
 [创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)   
 [MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)   
 [使用类编写 Windows 应用程序](../../mfc/using-the-classes-to-write-applications-for-windows.md)
