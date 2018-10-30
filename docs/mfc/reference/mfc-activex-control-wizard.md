---
title: MFC ActiveX 控件向导 |Microsoft Docs
ms.custom: ''
ms.date: 09/12/2018
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.overview
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [MFC], MFC
- MFC ActiveX controls [MFC], wizards
- OLE controls [MFC], creating
- MFC ActiveX Control Wizard
- OLE controls [MFC]
ms.assetid: f19d698c-bdc3-4c74-af97-3d6ccb441b75
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 09a4cdccf92df9681a85a03369ad0ba1792a6b25
ms.sourcegitcommit: a3c9e7888b8f437a170327c4c175733ad9eb0454
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/29/2018
ms.locfileid: "50204725"
---
# <a name="mfc-activex-control-wizard"></a>MFC ActiveX 控件向导

ActiveX 控件是特定类型的[自动化服务器](../../mfc/automation-servers.md); 它是可重用组件。 承载 ActiveX 控件的应用程序是[自动化客户端](../../mfc/automation-clients.md)该控件。 如果你的目标是创建此类可重用的组件，然后使用此向导创建您的控件。 请参阅[MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)有关详细信息。

>[!IMPORTANT]
> ActiveX 是一项传统技术，不应使用新的开发。 有关取代 ActiveX 的现代技术的详细信息，请参阅[ActiveX 控件](../activex-controls.md)。

另外，可以创建自动化服务器 MFC 应用程序中使用[MFC 应用程序向导](../../mfc/reference/mfc-application-wizard.md)。

使用此向导所创建的 ActiveX 控件可以具有用户界面，也可以是不可见。 您可以指示在此选项[控制设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)向导中的页。 计时器控件是你想要为不可见的 ActiveX 控件的示例。

ActiveX 控件可以具有复杂的用户界面。 某些控件可能类似于封装窗体： 一个控件包含许多字段，每个中自己的权限的 Windows 控件。 例如，作为 MFC ActiveX 控件实现的自动部件对象可能会显示类似于窗体的用户界面通过该用户可以读取和编辑的部件号、 部分构成的名称和其他信息。 请参阅[MFC ActiveX 控件](../../mfc/mfc-activex-controls.md)有关详细信息。

如果需要创建 ActiveX 对象的容器，请参阅[创建 ActiveX 控件容器](../../mfc/reference/creating-an-mfc-activex-control-container.md)。

MFC starter 项目包括 c + + 源文件 (.cpp)、 资源 (.rc) 文件和项目 (.vcxproj) 文件。 在这些初学者文件中生成的代码基于 MFC。

下面的示例列表显示了任务和类型的增强功能的 ActiveX 控件：

- [优化 ActiveX 控件](../../mfc/mfc-activex-controls-optimization.md)

- [向 ActiveX 控件添加常用事件](../../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [添加自定义事件](../../mfc/mfc-activex-controls-adding-custom-events.md)

- [添加常用方法](../../mfc/mfc-activex-controls-adding-stock-methods.md)

- [添加自定义方法](../../mfc/mfc-activex-controls-adding-custom-methods.md)

- [添加常用属性](../../mfc/mfc-activex-controls-adding-stock-properties.md)

- [添加自定义属性](../../mfc/mfc-activex-controls-adding-custom-properties.md)

- [ActiveX 控件容器中的 ActiveX 控件编程](../../mfc/programming-activex-controls-in-a-activex-control-container.md)

## <a name="overview"></a>概述

此向导页描述正在创建的 MFC ActiveX 控件项目的当前应用程序设置。 默认情况下，该向导创建一个项目，如下所示：

- 默认项目会生成任何运行时许可证或帮助文件。 您可以在更改这些默认设置[应用程序设置](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)页。 仅在 ActiveX 控件向导的此页所做的选择会反映在**概述**页。

- 该项目包括控制类和属性页类，基于项目的名称。 您可以在编辑你的项目和文件名称的名称[控件名称](../../mfc/reference/control-names-mfc-activex-control-wizard.md)页。

- 控件基于现有 Windows 控件，当它变得可见，有一个用户界面，并且包括激活**有关**对话框。 您可以在更改这些默认设置[控制设置](../../mfc/reference/control-settings-mfc-activex-control-wizard.md)页。

## <a name="see-also"></a>请参阅

[创建和管理 Visual C++ 项目](../../ide/creating-and-managing-visual-cpp-projects.md)<br/>
[Visual C++ 项目类型](../../ide/visual-cpp-project-types.md)<br/>
[概念](../../atl/active-template-library-atl-concepts.md)

