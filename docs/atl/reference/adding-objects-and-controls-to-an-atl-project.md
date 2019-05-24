---
title: 将对象和控件添加到 ATL 项目
ms.date: 05/09/2019
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
ms.openlocfilehash: deaac8f2d6aac02d0cd751e6abebb3b67051200f
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/15/2019
ms.locfileid: "65706851"
---
# <a name="adding-objects-and-controls-to-an-atl-project"></a>将对象和控件添加到 ATL 项目

> [!NOTE] 
> ATL COM+ 1.0 组件向导、ATL OLE DB 使用者向导和 ATL Active Server Page 组件向导在 Visual Studio 2019 及更高版本中不可用。

可以使用一个 ATL 代码向导将对象或控件添加到基于 ATL 或 MFC 的项目中。 对于添加的每个 COM 对象或控件，向导会生成 .cpp 和 .h 文件，以及基于脚本的注册表支持的 .rgs 文件。 Visual Studio 中提供了以下 ATL 代码向导：

||||
|-|-|-|
|[ATL 简单对象](../../atl/reference/atl-simple-object-wizard.md)|[ATL 对话框](../../atl/reference/atl-dialog-wizard.md)|[ATL 控件](../../atl/reference/atl-control-wizard.md)|
|[ATL 属性页](../../atl/reference/atl-property-page-wizard.md)|[ATL Active Server Page 组件](../../atl/reference/atl-active-server-page-component-wizard.md)|[ATL OLE DB 使用者](../../atl/reference/atl-ole-db-consumer-wizard.md)|
|[向 MFC 添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)|[ATL COM+ 1.0 组件向导](../../atl/reference/atl-com-plus-1-0-component-wizard.md)|[ATL OLE DB 提供程序](../../atl/reference/atl-ole-db-provider-wizard.md)|

> [!NOTE]
> 在将 ATL 对象添加到项目之前，应在相关的帮助主题中查看对象的详细信息和要求。

## <a name="to-add-an-object-or-a-control-using-the-atl-control-wizard"></a>使用 ATL 控件向导添加对象或控件

1. 在“解决方案资源管理器”中，右键单击项目节点，然后单击快捷菜单中的“添加”。 单击“添加类”。

   随即将显示[“添加类”](../../ide/add-class-dialog-box.md)对话框。

1. 在“类别”窗格中选择 ATL 文件夹后，从“模板”窗格中选择要插入的对象。 单击“打开”。 随即将显示所选对象的代码向导。

   > [!NOTE]
   > 如果要将 ATL 对象添加到 MFC 项目，则必须向现有项目添加 ATL 支持。 可以按照[向 MFC 项目添加 ATL 支持](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)中的说明来执行此操作。

   或者，如果尝试在未事先添加 ATL 支持的情况下将 ATL 对象添加到 MFC 项目，Visual Studio 会提示你指定是否要向项目添加 ATL 支持。 单击“是”向项目添加 ATL 支持并打开所选的 ATL 向导。

## <a name="see-also"></a>请参阅

[ATL 项目向导](../../atl/reference/atl-project-wizard.md)<br/>
[Visual Studio 中的 C++ 项目类型](../../build/reference/visual-cpp-project-types.md)<br/>
[ATL COM 对象基础知识](../../atl/fundamentals-of-atl-com-objects.md)<br/>
[使用 ATL 和 C 运行时代码进行编程](../../atl/programming-with-atl-and-c-run-time-code.md)<br/>
[默认 ATL 项目配置](../../atl/reference/default-atl-project-configurations.md)
