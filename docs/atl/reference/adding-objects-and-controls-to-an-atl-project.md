---
title: 将对象和控件添加到 ATL 项目
ms.date: 11/04/2016
f1_keywords:
- vc.appwiz.ATL.controls
helpviewer_keywords:
- ATL projects, adding objects
- wizards [C++], ATL projects
- ATL projects, adding controls
- controls [ATL], adding to projects
- objects [C++], adding to ATL projects
- ATL Control Wizard
ms.assetid: c0adcbd0-07fe-4c55-a8fd-8c2c65ecdaad
ms.openlocfilehash: 0577788e4ab28139943da4b3bd14914799341213
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50506127"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>将对象和控件添加到 ATL 项目

可以使用 ATL 代码向导之一来向基于 ATL 或 MFC 项目添加对象或控件。 对于每个 COM 对象或控件添加，向导将生成.cpp 和.h 文件，以及基于脚本的注册表支持 rgs 文件。 Visual Studio 中提供了以下的 ATL 代码向导：

||||
|-|-|-|
|[ATL 简单对象](../../atl/reference/atl-simple-object-wizard.md)|[ATL 对话框](../../atl/reference/atl-dialog-wizard.md)|[ATL 控件](../../atl/reference/atl-control-wizard.md)|
|[ATL 属性页](../../atl/reference/atl-property-page-wizard.md)|[ATL Active Server Page 组件](../../atl/reference/atl-active-server-page-component-wizard.md)|[ATL OLE DB 使用者](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[向 MFC 添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[ATL COM+ 1.0 组件向导](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[ATL OLE DB 访问接口](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> 在 ATL 对象添加到你的项目之前, 应查看的详细信息和要求的相关帮助主题中的对象。

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>若要添加对象或使用 ATL 控件向导控件

1. 在中**解决方案资源管理器**，右键单击项目节点，然后单击**添加**从快捷菜单。 单击**将类添加**。

   [添加类](../../ide/add-class-dialog-box.md)对话框随即出现。

1. 与**ATL**中所选文件夹**类别**窗格中，选择一个要插入从对象**模板**窗格。 单击**打开**。 将显示所选对象代码向导。

   > [!NOTE]
   > 如果你想要向 MFC 项目添加 ATL 对象，您必须向现有项目添加 ATL 支持。 可以为此中的说明[向 MFC 项目添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)。

   或者，如果尝试向 MFC 项目添加 ATL 对象，而无需以前添加 ATL 支持，Visual Studio 会提示你指定是否希望 ATL 支持添加到你的项目。 单击**是**向项目添加 ATL 支持，并打开所选的 ATL 向导。

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)<br/>
[Visual C++ 项目类型](../../ide/visual-cpp-project-types.md)<br/>
[使用应用程序向导创建桌面项目](../../ide/creating-desktop-projects-by-using-application-wizards.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)
