---
title: 如何： 使用资源模板 （c + +） |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- language-specific template files [C++]
- resource templates
- resources [C++], creating
- rct files [C++]
- templates, resource templates
- resources [C++], templates
- .rct files [C++]
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 677828343fa7247e64a8dfbd8faede4efbc9df24
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2018
ms.locfileid: "46393745"
---
# <a name="how-to-use-resource-templates-c"></a>如何： 使用资源模板 （c + +）

资源模板是保存为 .rct 文件的自定义资源。 因此，可将资源模板视为创建其他资源的起点。 资源模板可节省开发其他资源或共享功能（如标准控件和其他重复元素）的资源组的时间。 例如，你可能希望在多个对话框中包含“帮助”按钮和公司徽标的图标。 若要快速做到这一点，可以新建一个对话框模板，并用徽标和“帮助”按钮对其进行自定义。

一旦自定义资源模板之后，必须将所做的更改保存在模板文件夹 （或 include 路径中指定的任何位置），以便新的资源模板将显示中的资源类型下[添加资源对话框](../windows/add-resource-dialog-box.md). 然后，你可以根据需要像往常一样使用资源模板。

> [!NOTE]
> 你可以将语言特定的模板文件放在主模板目录的子目录中。 例如，将仅限英语的模板文件放\\< 资源模板目录\>\1033。

### <a name="to-create-a-template-for-resources"></a>若要创建资源模板

1. 在中**解决方案资源管理器**，右键单击你的项目。

2. 从快捷菜单中，选择**外**，然后单击**添加新项**。

3. 在中**添加新项**对话框中**模板：** 窗格中，选择**资源模板文件 (.rct)**。

4. 提供的名称和新的.rct 文件的位置，然后单击**打开**。

5. 新的.rct 文件添加到你的项目，并显示在**解决方案资源管理器**下**资源**文件夹。

   现在，可以双击.rct 文件以在文档窗口中，将其打开，然后将资源添加到其中 (右键单击文档窗口中的文件，然后选择**添加资源**从快捷菜单)。 这时，你便可以自定义这些资源并保存为 .rct 文件了。

   > [!NOTE]
   > 创建新的 RCT 文件时，Visual Studio 将在 \Program Files\Microsoft Visual Studio 9.0\vc\vcresourcetemplates、\program \Program Files\Microsoft Visual Studio 9.0\vc\vcresourcetemplates、\program\\*LCID* (例如 1033 为英语)，*或*上的任何位置[包括路径](../windows/how-to-specify-include-directories-for-resources.md)。 如果你想将 RCT 文件保存到另一个文件夹，例如 \My Documents，则只需将此文件夹添加到 include 路径，Visual Studio 就会查找该 RCT 文件。

### <a name="to-convert-an-existing-rc-file-to-an-rct-file"></a>若要将现有的 .rc 文件转换为 .rct 文件

1. [将.rc 文件作为一个独立的文件打开](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。

2. 上**文件**菜单上，单击**保存\<*你的文件名*> 为**。

3. 指定一个位置，然后单击**确定**。

### <a name="to-create-a-new-resource-from-a-template"></a>若要从模板创建新资源

1. 在中[资源视图](../windows/resource-view-window.md)窗格中，右键单击.rc 文件，然后选择**添加资源**从快捷菜单。

2. 在中**添加资源**对话框框中，单击加号 (**+**) 旁边的展开资源节点，查看可用于该资源的所有模板的资源。

3. 双击要使用的模板。

4. 根据需要在相应的资源编辑器中修改已添加的资源。

   资源编辑器将自动提供一个唯一的资源 ID。 您可以修订[资源属性](../windows/changing-the-properties-of-a-resource.md)根据需要。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。

## <a name="requirements"></a>要求

Win32

## <a name="see-also"></a>请参阅

[资源文件](../windows/resource-files-visual-studio.md)<br/>
[资源编辑器](../windows/resource-editors.md)