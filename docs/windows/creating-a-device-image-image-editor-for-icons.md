---
title: 创建设备图像（图标的图像编辑器）
ms.date: 11/04/2016
f1_keywords:
- vc.editors.icon
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices [C++], creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
ms.openlocfilehash: 322205e22edf2624784ddb8f294bcf5e73af06f7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50447745"
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>创建设备图像（图标的图像编辑器）

当创建新图标或光标资源**图像**编辑器首先在特定样式 （32 × 32，16 种颜色图标和 32 × 32，游标的单色） 中创建映像。 然后可以将不同大小和样式的图像添加到初始图标或光标，并编辑每个其他映像，根据需要对不同的显示设备。 此外可以通过从现有的映像类型或从位图图形程序创建的执行剪切和粘贴操作来编辑映像。

当你打开中的图标或光标资源[的图像编辑器](../windows/image-editor-for-icons.md)，默认情况下将打开大多数紧密匹配当前的显示设备的图像。

### <a name="to-create-a-new-icon-or-cursor"></a>若要创建新图标或光标

1. 在中[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果已有现有的图像资源在.rc 文件中，例如游标，只需可以右击**游标**文件夹，然后选择**插入光标**从快捷菜单。)

   > [!NOTE]
   > 如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。

2. 在中[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**游标**然后单击**新建**。 对于图标，这将创建一个图标资源使用 32 × 32，16 色图标。 对于游标，32 × 32，创建单色 （2 种颜色） 映像。

   如果一个加号 (**+**) 中的图像资源类型旁边会显示**插入资源**对话框中，这意味着工具栏模板都可用。 单击加号以展开模板列表中的，选择一个模板，然后单击**新建**。

有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。

## <a name="requirements"></a>要求

无

## <a name="see-also"></a>请参阅

[图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)<br/>
[加速键](../windows/accelerator-keys-image-editor-for-icons.md)<br/>
[图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)