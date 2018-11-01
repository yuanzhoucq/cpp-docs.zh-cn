---
title: 创建新的工具栏按钮 （c + +）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.toolbar
helpviewer_keywords:
- Toolbar editor [C++], creating buttons
- toolbar buttons [C++], button image
- toolbar buttons [C++], creating
- toolbar buttons (in Toolbar editor)
ms.assetid: 46c120fe-4f2a-4887-a08f-bd1fea04b3f4
ms.openlocfilehash: 1fe3e960ea9d2cec36e1c0d1ee9edb30bcc354d4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50512497"
---
# <a name="creating-a-new-toolbar-button-c"></a>创建新的工具栏按钮 （c + +）

### <a name="to-create-a-new-toolbar-button"></a>若要创建新的工具栏按钮

1. 在中[资源视图](../windows/resource-view-window.md)展开资源文件夹 (如 Project1.rc)。

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 展开**工具栏**文件夹，然后选择要编辑的工具栏。

3. 将 ID 分配给工具栏右侧的空白按钮。 您可以通过编辑来实现**ID**属性中的[属性窗口](/visualstudio/ide/reference/properties-window)。 例如，你可能想要提供的工具栏按钮和菜单选项相同的 ID。 在这种情况下，使用下拉列表框选择**ID**的菜单选项。

   或

   选择工具栏右侧的空白按钮 (在**工具栏视图**窗格) 并开始绘制。 分配一个默认按钮命令 ID (ID_BUTTON\<n >)。

您还可以复制并粘贴到为新按钮的工具栏上的图像。

### <a name="to-add-an-image-to-a-toolbar-as-a-button"></a>若要将图像添加到工具栏中，为的按钮

1. 在中[资源视图](../windows/resource-view-window.md)，通过双击它打开工具栏。

2. 接下来，打开你想要添加到您的工具栏图像。

   > [!NOTE]
   > 如果您在 Visual Studio 中打开该映像，将在中打开**图像**编辑器。 此外可以在其他图形程序中打开的图像。

3. 从**编辑**菜单中，选择**副本**。

4. 通过单击其选项卡顶部的源窗口中切换到您的工具栏。

5. 从**编辑**菜单中，选择**粘贴**。

   图像将显示在工具栏上，为新按钮。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

MFC 或 ATL

## <a name="see-also"></a>请参阅

[工具栏按钮属性](../windows/toolbar-button-properties.md)<br/>
[创建、移动和编辑工具栏按钮](../windows/creating-moving-and-editing-toolbar-buttons.md)<br/>
[工具栏编辑器](../windows/toolbar-editor.md)