---
title: 创建文件资源管理器样式的 MFC 应用程序 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfcexplorer.project
dev_langs:
- C++
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2a2c3e8e1c7956a5dff33cd8ff78612f5f844ad6
ms.sourcegitcommit: be0e3457f2884551f18e183ef0ea65c3ded7f689
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 06/28/2018
ms.locfileid: "37078416"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>创建文件资源管理器样式的 MFC 应用程序
许多 Windows 系统应用程序为文件资源管理器使用用户界面 (UI)。 当你启动文件资源管理器时，例如，你看到具有垂直拆分条分割的工作区的应用程序。 客户端区域的左侧提供导航和浏览功能，并右端的客户端区域显示详细信息与所选内容相关的左窗格中。 当用户单击左窗格中的项时，应用程序重新填充右侧窗格。 在 MDI 应用程序，可以使用命令，在**视图**菜单更改显示在右窗格中的详细信息量。 （在 SDI 或多个顶级文档应用程序中，可以更改使用的工具栏按钮的详细信息。）  
  
 窗格的内容取决于应用程序。 在文件系统浏览器中，左窗格中显示目录或的计算机或计算机组的分层的视图，而右窗格中显示的文件夹、 单个文件，或机和它们的详细信息。 内容一定不需要是文件。 它们可能是电子邮件消息、 错误报告或在数据库中的其他项。  
  
 向导为你创建的以下类：  
  
-   `CLeftView`类定义的工作区的左窗格。 它始终派生自[CTreeView](../../mfc/reference/ctreeview-class.md)。  
  
-   C*ProjName*视图类定义的工作区的右窗格。 默认情况下，它派生自[CListView](../../mfc/reference/clistview-class.md)但可以是另一种具体取决于您指定的类的视图**基类**列入[生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页向导。  
  
 生成的应用程序可以具有单文档界面 (SDI)、 多文档界面 (MDI) 或多个顶级文档体系结构。 应用程序创建每个框架窗口垂直拆分使用[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)。 编码此应用程序类型是类似于编码的正常的 MFC 应用程序使用拆分器，只不过此类型的应用程序包含每个拆分器窗格中的单独的控件视图。  
  
 如果在右窗格中使用的默认列表视图，该向导将创建额外的菜单选项 （在 MDI 应用程序仅） 和工具栏按钮以切换在大图标、 小图标、 列表和详细信息模式之间的视图的样式。  
  
### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>若要开始创建文件资源管理器样式的 MFC 可执行文件  
  
1.  按照中的说明[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)。  
  
2.  在 MFC 应用程序向导[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页上，选择**文件资源管理器**项目样式。  
  
3.  在向导的其他页面上设置所需的任何其他选项。  
  
4.  单击**完成**生成主干应用程序。  
  
 有关详细信息，请参见:  
  
-   [多文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)  
  
-   [派生的视图类](../../mfc/derived-view-classes-available-in-mfc.md)  
  
-   [应用程序设计选项](../../mfc/application-design-choices.md)  
  
## <a name="see-also"></a>请参阅  
 [MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)   
 [创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)   
 [创建基于窗体的 MFC 应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)

