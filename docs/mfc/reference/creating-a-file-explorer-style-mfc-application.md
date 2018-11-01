---
title: 创建文件资源管理器样式的 MFC 应用程序
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.mfcexplorer.project
helpviewer_keywords:
- browsers [MFC], Explorer-style applications
- MFC applications [MFC], Windows Explorer-style
- Explorer-style applications [MFC], creating
ms.assetid: f843ab5d-2d5d-41ca-88a4-badc0d2f8052
ms.openlocfilehash: 3ddeb2e875ccdb45dd0bc2b29a2da3c1498138ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564757"
---
# <a name="creating-a-file-explorer-style-mfc-application"></a>创建文件资源管理器样式的 MFC 应用程序

许多 Windows 系统应用程序将文件资源管理器用户界面 (UI)。 当您启动文件资源管理器时，例如，您看到具有垂直拆分条分割的客户端区域的应用程序。 左侧和右侧的工作区提供导航和浏览功能和客户端区域的右侧显示的详细信息与所选内容相关的左窗格中。 当用户单击左窗格中的项时，应用程序重新填充的右窗格。 在 MDI 应用程序，可以在使用命令**视图**菜单更改显示在右窗格中的详细信息量。 （在 SDI 或多个顶级文档应用程序中，可以更改使用的工具栏按钮的详细信息。）

在窗格的内容取决于应用程序。 在文件系统浏览器中，左窗格中显示目录或计算机或计算机组的分层的视图，而右窗格中显示的文件夹、 单独的文件，或计算机和它们的详细信息。 内容一定不需要的文件。 它们可能是电子邮件消息、 错误报告或在数据库中的其他项。

该向导将创建以下类：

- `CLeftView`类定义的工作区的左窗格。 它始终派生自[CTreeView](../../mfc/reference/ctreeview-class.md)。

- C*ProjName*视图类定义的客户端区域的右窗格。 默认情况下，它派生自[CListView](../../mfc/reference/clistview-class.md)可以是另一种具体取决于从指定的类的视图，但**基类**列表中[生成的类](../../mfc/reference/generated-classes-mfc-application-wizard.md)页向导。

生成的应用程序可以具有单文档界面 (SDI)、 多文档界面 (MDI) 或多个顶级文档结构。 应用程序会创建每个框架窗口垂直拆分使用[CSplitterWnd](../../mfc/reference/csplitterwnd-class.md)。 编码此应用程序类型是类似于编码使用拆分器的正常 MFC 应用程序，只不过此类型的应用程序都有单独的控件视图中每个拆分器窗格。

如果在右窗格中使用的默认列表视图，该向导将创建额外的菜单选项 （在 MDI 应用程序仅） 和工具栏按钮以切换在大图标、 小图标、 列表和详细信息模式之间的视图的样式。

### <a name="to-begin-creating-a-file-explorer-style-mfc-executable"></a>若要开始创建的文件资源管理器样式的 MFC 可执行文件

1. 按照中的说明[创建 MFC 应用程序](../../mfc/reference/creating-an-mfc-application.md)。

1. 在 MFC 应用程序向导[应用程序类型](../../mfc/reference/application-type-mfc-application-wizard.md)页上，选择**文件资源管理器**项目样式。

1. 在向导的其他页面上设置所需的任何其他选项。

1. 单击**完成**生成主干应用程序。

有关详细信息，请参见:

- [多文档类型、视图和框架窗口](../../mfc/multiple-document-types-views-and-frame-windows.md)

- [派生的视图类](../../mfc/derived-view-classes-available-in-mfc.md)

- [应用程序设计选项](../../mfc/application-design-choices.md)

## <a name="see-also"></a>请参阅

[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)<br/>
[创建 Web 浏览器样式的 MFC 应用程序](../../mfc/reference/creating-a-web-browser-style-mfc-application.md)<br/>
[创建基于窗体的 MFC 应用程序](../../mfc/reference/creating-a-forms-based-mfc-application.md)

