---
title: 创建设备图像 （图标的图像编辑器） |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.icon
dev_langs:
- C++
helpviewer_keywords:
- cursors [C++], creating
- icons [C++], creating
- display devices
- display devices, creating image
- images [C++], creating for display devices
- icons [C++], inserting
ms.assetid: 5a536928-32df-4ace-beb1-1521ce3b871f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d8fc1ce4bd5a6e125ece7461d100950f255dee44
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-device-image-image-editor-for-icons"></a>创建设备图像（图标的图像编辑器）
当你创建新图标或光标资源时，图像编辑器首先以特定的样式 （32 × 32，16 种颜色图标和 32x32，为游标的单色） 创建的映像。 然后可以将映像中不同的大小和样式添加到初始图标或光标，并编辑每个其他映像，根据需要为不同的显示设备。 你还可以通过执行剪切和粘贴操作，从现有的映像类型或在图形程序中创建的位图编辑映像。  
  
 当你打开中的图标或光标资源[图像编辑器](../windows/image-editor-for-icons.md)，默认情况下将打开大多数密切匹配的当前的显示设备的图像。  
  
### <a name="to-create-a-new-icon-or-cursor"></a>若要创建新图标或光标  
  
1.  在[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果你已有现有的图像资源在.rc 文件中，如游标，只需可以右键单击**光标**文件夹，然后选择**插入光标**从快捷菜单。)  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入资源对话框](../windows/add-resource-dialog-box.md)，选择**图标**或**光标**单击**新建**。 对于图标，这将创建一个图标资源 32 × 32，16 颜色图标。 对于光标，32x32，创建单色 （2 种颜色） 映像。  
  
     如果一个加号 (**+**) 旁边图像资源类型显示**插入资源**对话框中，这意味着工具栏模板都可用。 单击加号以便展开模板列表中的，选择一个模板，然后单击**新建**。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 **要求**  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [快捷键](../windows/accelerator-keys-image-editor-for-icons.md)   
 [图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)
