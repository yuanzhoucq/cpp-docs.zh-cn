---
title: "查看和编辑资源在资源编辑器中 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.resourceview
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- rc files, viewing resources
- Resource View pane
- layouts, previewing resource
- code, viewing resources
- resource editors, viewing resources
- .rc files, viewing resources
- resources [Visual Studio], editing
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 980264ab1857af214dcd24703980b8efa9a4d2dd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="viewing-and-editing-resources-in-a-resource-editor"></a>在资源编辑器中查看和编辑资源
每个资源类型都有特定于该资源类型的资源编辑器。 你可以重新排列、 调整大小、 添加控件和功能，或修改资源使用关联的编辑器的方面。 你还可以编辑中的资源[文本格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)和[二进制格式](../windows/opening-a-resource-for-binary-editing.md)。  
  
 某些资源类型是单个文件可以导入并使用以各种方式;其中包括位图、 图标、 光标、 工具栏和 html 文件。 此类资源的文件名，以及[资源标识符](../windows/symbols-resource-identifiers.md)。 其他，例如对话框、 菜单和字符串表在 Win32 项目中，仅作为的一部分存在的资源脚本 (.rc) 文件或资源模板 (.rct) 文件。  
  
> [!NOTE]
>  资源属性[可以使用属性窗口修改](../windows/changing-the-properties-of-a-resource.md)。  
  
## <a name="win32-resources"></a>Win32 资源  
 你可以访问中的 Win32 资源[资源视图](../windows/resource-view-window.md)窗格。  
  
#### <a name="to-view-a-win32-resource-in-a-resource-editor"></a>若要在资源编辑器中查看 Win32 资源  
  
1.  选择**资源视图**从**视图**菜单。  
  
2.  如果资源视图窗口不是最顶端窗口，请单击**资源视图**选项卡以在顶部显示它。  
  
3.  从资源视图中，展开包含你想要查看的资源的项目的文件夹。 例如，如果你想要查看对话框资源，则展开对话框文件夹。  
  
    > [!NOTE]
    >  如果你的项目尚未包含 .rc 文件，请参阅 [创建新的资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
4.  双击该资源，例如，IDD_ABOUTBOX。  
  
     资源将在适当的编辑器中打开。 例如，对于对话框资源，资源在对话框编辑器打开。  
  
     你还可以[.rc （资源脚本） 文件中查看资源，而无需打开一个项目](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
#### <a name="to-delete-an-existing-win-32-resource"></a>若要删除现有的 Win 32 资源  
  
1.  在资源视图中，展开资源类型的节点。  
  
2.  右键单击你想要删除选择的资源**删除**从快捷菜单。  
  
    > [!NOTE]
    >  您可以删除某个资源具有已在项目外部文档窗口中打开.rc 文件时使用相同的快捷菜单命令。  
  
## <a name="resources-in-managed-projects"></a>在托管项目中的资源  
 因为托管的项目不使用资源脚本文件，则必须打开您的资源不**解决方案资源管理器**。 你可以使用[图像编辑器](../windows/image-editor-for-icons.md)和[二进制编辑器](binary-editor.md)处理的托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
#### <a name="to-view-a-managed-resource-in-a-resource-editor"></a>若要在资源编辑器中查看托管的资源  
  
1.  在解决方案资源管理器中，双击资源，例如，Bitmap1.bmp。  
  
     资源将在适当的编辑器中打开。  
  
#### <a name="to-delete-an-existing-managed-resource"></a>若要删除现有的托管的资源  
  
1.  在解决方案资源管理器，右键单击你想要删除选择的资源**删除**从快捷菜单。  
  
### <a name="requirements"></a>惠?  
 无  
  
## <a name="see-also"></a>请参阅  
 [资源编辑器](../windows/resource-editors.md)

