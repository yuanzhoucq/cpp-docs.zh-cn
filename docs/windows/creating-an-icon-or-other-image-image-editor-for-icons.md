---
title: "创建图标或其他图像 （图标的图像编辑器） |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.bitmap
dev_langs: C++
helpviewer_keywords:
- bitmaps [C++]
- images [C++], creating
- resource toolbars
- resources [Visual Studio], creating images
- bitmaps [C++], creating
- graphics [C++], creating
- Image editor [C++], creating images
ms.assetid: 66db3fb2-cfc1-48a2-9bdd-53f61eb7ee30
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ae1cc8525b0c93cff5564c2185d80480a632718b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="creating-an-icon-or-other-image-image-editor-for-icons"></a>创建图标或其他图像（图标的图像编辑器）
你可以创建新映像 （位图、 图标、 光标或工具栏），然后使用图像编辑器自定义其外观。 你还可以创建新的位图模式[模板](../windows/how-to-use-resource-templates.md)。  
  
### <a name="to-add-a-new-image-resource-to-an-unmanaged-c-project"></a>若要向非托管 c + + 项目中添加新的图像资源  
  
1.  在[资源视图](../windows/resource-view-window.md)，右键单击.rc 文件，然后选择**插入资源**从快捷菜单。 (如果你已有现有的图像资源在.rc 文件中，如游标，只需可以右键单击**光标**文件夹，然后选择**插入光标**从快捷菜单。)  
  
    > [!NOTE]
    >  **注意：** 如果你的项目尚未包含 .rc 文件，请参阅 [创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[插入资源对话框](../windows/add-resource-dialog-box.md)，选择想要创建的图像资源的类型 (**位图**，例如) 然后单击**新建**。  
  
     如果一个加号 (**+**) 旁边图像资源类型显示**插入资源**对话框中，这意味着工具栏模板都可用。 单击加号以便展开模板列表中的，选择一个模板，然后单击**新建**。  
  
### <a name="to-add-a-new-image-resource-to-a-project-in-a-net-programming-language"></a>若要将新的映像资源添加到一种.NET 编程语言中的项目  
  
1.  在**解决方案资源管理器**，右击项目文件夹 (例如， **WindowsApplication1**)。  
  
2.  从快捷菜单中，单击**添加**，然后选择**添加新项**。  
  
3.  在**类别**窗格中，展开**本地项目项**文件夹，然后选择**资源**。  
  
4.  在**模板**窗格中，选择想要添加到你的项目的资源类型。  
  
     资源添加到你的项目在解决方案资源管理器并在中打开该资源[图像编辑器](../windows/image-editor-for-icons.md)。 你现在可以使用图像编辑器中可用的所有工具修改你的映像。 将映像添加到托管项目的详细信息，请参阅[加载在设计时图片](/dotnet/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms)。  
  
    > [!NOTE]
    >  你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。 有关详细信息，请参阅[创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)中*.NET Framework 开发员指南*。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 惠?  
  
 无  
  
## <a name="see-also"></a>请参阅  
 [图标和光标： 显示设备的图像资源](../windows/icons-and-cursors-image-resources-for-display-devices-image-editor-for-icons.md)   
 [将位图转换为工具栏](../windows/converting-bitmaps-to-toolbars.md)   
 [创建新工具栏](../windows/creating-new-toolbars.md)   
 [编辑图形资源](../windows/editing-graphical-resources-image-editor-for-icons.md)   
 [图标的图像编辑器](../windows/image-editor-for-icons.md)

