---
title: 如何： 复制资源 |Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.copying
- vs.resvw.resource.copying
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], moving between files
- resources [Visual Studio], copying
- resource files, copying or moving resources between
- resource files, tiling
- .rc files, copying resources between
- rc files, copying resources between
ms.assetid: 65f523e8-017f-4fc6-82d1-083c56d9131f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4b173be24e9f177a3156f740fcb07240c30fec75
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/08/2018
ms.locfileid: "33879843"
---
# <a name="how-to-copy-resources"></a>如何：复制资源
你可以复制资源从一个文件到另一个不加更改地或者你可以[同时将它复制更改的语言或资源的条件](../windows/how-to-change-the-language-or-condition-of-a-resource-while-copying.md)。  
  
 可以轻松地从现有资源或可执行文件的资源复制到您的当前资源文件。 若要执行此操作，你打开这两个文件同时包含资源和将项从一个文件拖动到另一个或复制并粘贴在两个文件之间。 此方法适用于资源脚本 (.rc) 文件和资源模板 (.rct) 文件，以及可执行文件 (.exe) 文件。  
  
> [!NOTE]
>  Visual c + + 包括可以在自己的应用程序中使用的示例资源文件。 有关详细信息，请参阅[剪贴画： 公共资源](http://msdn.microsoft.com/en-us/9bac2891-b6b3-49ec-a287-cec850c707e0)。  
  
 你可以打开.rc 文件之间使用拖放方法[项目之外](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
### <a name="to-copy-resources-between-files-using-the-drag-and-drop-method"></a>若要使用拖放方法的文件之间复制资源  
  
1.  打开两个独立的资源文件 (有关详细信息，请参阅[查看.rc 文件之外的项目中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，打开 Source1.rc 和 Source2.rc。  
  
2.  在第一个.rc 文件中，单击你想要复制的资源。 例如，在 Source1.rc，请单击 IDD_DIALOG1。  
  
3.  按住 CTRL 键并将资源拖到第二个.rc 文件。 例如，将从 Source1.rc 的 IDD_DIALOG1 拖到 Source2.rc 中。  
  
    > [!NOTE]
    >  没有按住 CTRL 键拖动资源移动资源，而不是将其复制。  
  
### <a name="to-copy-resources-using-copy-and-paste"></a>复制资源使用复制和粘贴  
  
1.  打开两个独立的资源文件 (有关详细信息，请参阅[查看.rc 文件之外的项目中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md))。 例如，Source1.rc 和 Source2.rc。  
  
2.  在源代码文件中你想要复制资源 (例如，Source1.rc)，右键单击资源，然后选择**复制**从快捷菜单。  
  
3.  右键单击要在其中粘贴资源 (例如，Source2.rc) 的资源文件。 选择**粘贴**从快捷菜单。  
  
    > [!NOTE]
    >  你不能拖放、 复制、 剪切、 或粘贴项目 （资源视图中） 中的资源文件和独立.rc 文件 （那些在文档窗口中打开） 之间。 在以前版本的产品，无法执行此操作。  
  
    > [!NOTE]
    >  若要避免与符号名称或现有文件中的值冲突，Visual c + + 可能会更改传输的资源的符号值或符号名称和值时将其复制到新文件。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 要求  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何： 打开项目 （独立） 外部的资源脚本文件](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [资源文件](../windows/resource-files-visual-studio.md)   
 [资源编辑器](../windows/resource-editors.md)