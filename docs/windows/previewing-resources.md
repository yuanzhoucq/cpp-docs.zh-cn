---
title: "预览资源 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- resource previews
- code, viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0eca56e607c916e28afc7bf513d853bcf6d94b81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="previewing-resources"></a>预览资源
预览你的资源，可查看图形资源，而无需打开它们。 预览也是有用的可执行文件后你已编译它们，因为资源标识符将改为数字。 由于这些数字标识符通常不提供足够的信息，预览资源帮助你快速标识它们。  
  
 你可以预览以下资源类型的可视布局：  
  
-   Bitmap  
  
-   对话框  
  
-   图标  
  
-   菜单  
  
-   Cursor  
  
-   Toolbar  
  
 可视预览功能不适用于快捷键、 清单、 字符串表和版本信息资源。  
  
### <a name="to-preview-resources"></a>若要预览资源  
  
1.  在[资源视图](../windows/resource-view-window.md)或文档窗口中，选择你的资源，例如，IDD_ABOUTBOX。  
  
     **注意：** 如果你的项目尚未包含 .rc 文件，请参阅 [创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在[属性窗口](/visualstudio/ide/reference/properties-window)，单击**属性页**按钮。  
  
     \- 或 -  
  
3.  上**视图**菜单上，单击**属性页**。  
  
     资源的属性页将打开显示该资源的预览。 然后，你可以使用向上和向下箭头键导航资源视图或文档窗口中的树控件。 属性页上将保持打开状态，并显示的任何资源，具有焦点并且能够将预览。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中*.NET Framework 开发指南。* 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[对于桌面应用程序创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的资源在托管应用中的信息，请参阅[Globalizing 和本地化的.NET Framework 应用程序](/dotnet/standard/globalization-localization/index)。  
  
 **要求**  
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何： 打开项目 （独立） 外部的资源脚本文件](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [资源编辑器](../windows/resource-editors.md)

