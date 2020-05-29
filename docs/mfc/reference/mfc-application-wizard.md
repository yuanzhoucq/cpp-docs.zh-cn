---
title: MFC 应用程序向导
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfc.exe.overview
helpviewer_keywords:
- MFC Application Wizard
- executable files, creating
ms.assetid: 227ac090-921d-4b2f-be0a-66a5f4cab0d4
ms.openlocfilehash: 6949f136890e8274f225a49496b2eb1b8f78b6fc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81351835"
---
# <a name="mfc-application-wizard"></a>MFC 应用程序向导

MFC 应用程序向导生成一个应用程序，在编译时实现 Windows 可执行 （.exe） 应用程序的基本功能。 MFC 初学者应用程序包括C++源 （.cpp） 文件、资源 （.rc） 文件、标头 （.h） 文件和项目 （.vcxproj） 文件。 在这些初学者文件中生成的代码基于 MFC。

> [!NOTE]
> 根据您选择的选项，向导会在项目中创建其他文件。 例如，如果在["高级功能"](../../mfc/reference/advanced-features-mfc-application-wizard.md)页上选择**上下文相关帮助**，向导将创建编译项目帮助文件所需的文件。 有关向导创建的文件的详细信息，请参阅[为 Visual Studio C++项目创建的文件类型](../../build/reference/file-types-created-for-visual-cpp-projects.md)，并在项目中查看 Readme.txt 文件。

## <a name="overview"></a>概述

此向导页描述要创建的 MFC 应用程序的当前应用程序设置。 默认情况下，向导创建项目如下：

- [MFC 应用程序向导的应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)

  - 项目使用选项卡式多文档接口 （MDI） 支持创建。 有关详细信息，请参阅[SDI 和 MDI](../../mfc/sdi-and-mdi.md)。

  - 该项目使用[文档/视图体系结构](../../mfc/document-view-architecture.md)。

  - 该项目使用 Unicode 库。

  - 该项目使用 Visual Studio 项目样式创建，并支持视觉样式切换。

  - 项目在共享 DLL 中使用 MFC。 有关详细信息，请参阅[在可视化工作室中创建 C/C++ DLL。](../../build/dlls-in-visual-cpp.md)

- [MFC 应用程序向导的复合文档支持](../../mfc/reference/compound-document-support-mfc-application-wizard.md)

  - 该项目不提供复合文档的支持。

- [文档模板字符串，MFC 应用程序向导](../../mfc/reference/document-template-strings-mfc-application-wizard.md)

  - 项目使用项目名称作为默认文档模板字符串。

- [MFC 应用程序向导的数据库支持](../../mfc/reference/database-support-mfc-application-wizard.md)

  - 该项目不提供数据库支持。

- [MFC 应用程序向导的用户界面功能](../../mfc/reference/user-interface-features-mfc-application-wizard.md)

  - 该项目实现标准 Windows 用户界面功能，如系统菜单、状态栏、最大化和最小化框 **、"关于"** 框、标准菜单栏和停靠工具栏以及子框架。

- [MFC 应用程序向导的高级功能](../../mfc/reference/advanced-features-mfc-application-wizard.md)

  - 该项目支持打印和打印预览。

  - 该项目支持 ActiveX 控件。 有关详细信息，请参阅创建[ActiveX 控件的操作序列](../../mfc/sequence-of-operations-for-creating-activex-controls.md)。

  - 该项目不支持[自动化](../../mfc/automation.md)[、MAPI、Windows](../../mfc/mapi-support-in-mfc.md)[套接字](../../mfc/windows-sockets-in-mfc.md)或活动辅助功能。

  - 该项目支持**资源管理器**停靠窗格、**输出**停靠窗格和**属性**停靠窗格。

- [MFC 应用程序向导的生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)

  - 项目的视图类派生自[CView 类](../../mfc/reference/cview-class.md)。

  - 该项目的应用程序类派生自[CWinAppEx 类](../../mfc/reference/cwinappex-class.md)。

  - 项目的文档类派生自[CDocument 类](../../mfc/reference/cdocument-class.md)。

  - 该项目的主框架类派生自[CMDIFrameWndEx 类](../../mfc/reference/cmdiframewndex-class.md)。

  - 该项目的子框架类派生自[CMDIChildWndEx 类](../../mfc/reference/cmdichildwndex-class.md)。

要更改这些默认设置，请单击向导左列中的相应选项卡标题，然后对显示的页面上进行更改。

创建 MFC 应用程序项目后，可以使用 VisualC++[代码向导](../../ide/adding-functionality-with-code-wizards-cpp.md)向项目添加对象或控件。

## <a name="see-also"></a>另请参阅

[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)<br/>
[MFC 桌面应用程序](../../mfc/mfc-desktop-applications.md)<br/>
[使用类为 Windows 编写应用程序](../../mfc/using-the-classes-to-write-applications-for-windows.md)
