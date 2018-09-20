---
title: 创建图标或其他图像 （图标的图像编辑器） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.bitmap
dev_langs:
- C++
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resources [C++], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 43ba8086481ea2a8dde20d06b1dc143b297138f8
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46378301"
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>创建图标或其他图像（图标的图像编辑器）

可以创建新的映像 （位图、 图标、 游标或工具栏），然后使用图像编辑器自定义其外观。 此外可以创建新的位图采用[模板](../windows/how-to-use-resource-templates.md)。

### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>若要将新的图像资源添加到非托管的 c + + 项目

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果已有现有的图像资源在.rc 文件中，例如游标，只需可以右击**游标**文件夹，然后选择**插入光标**从快捷菜单。)

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择你想要创建的图像资源的类型 (**位图**，例如) 然后单击**新建**。

   如果一个加号 (**+**) 中的图像资源类型旁边会显示**插入资源**对话框中，这意味着工具栏模板都可用。 单击加号以展开模板列表中的，选择一个模板，然后单击**新建**。

### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>若要将新的图像资源添加到.NET 编程语言中的项目

1. 在中**解决方案资源管理器**，右键单击项目文件夹 (例如， `WindowsApplication1`)。

2. 从快捷菜单中，单击**外**，然后选择**添加新项**。

3. 在中**类别**窗格中，展开**本地项目项**文件夹，然后选择**资源**。

4. 在中**模板**窗格中，选择你想要添加到项目的资源类型。

   该资源添加到项目中**解决方案资源管理器**，并在打开该资源[图像编辑器](../windows/image-editor-for-icons.md)。 现在可以使用图像编辑器中可用的所有工具来修改你的映像。 将映像添加到托管项目的详细信息，请参阅[加载在设计时图片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。

   > [!NOTE]
   > 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。 有关详细信息，请参阅[创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)中 *.NET Framework 开发人员指南*。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[将位图转换为工具栏](../windows/converting-bitmaps-to-toolbars.md)<br/>
[创建新工具栏](../windows/creating-new-toolbars.md)<br/>
[编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)<br/>
[图标的图像编辑器](../windows/image-editor-for-icons.md)