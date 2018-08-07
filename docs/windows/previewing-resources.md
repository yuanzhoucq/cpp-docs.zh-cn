---
title: 预览资源 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0ff41dd0aad30382eb5229679054a74526652737
ms.sourcegitcommit: 4586bfc32d8bc37ab08b24816d7fad5df709bfa3
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 08/07/2018
ms.locfileid: "39605014"
---
# <a name="previewing-resources"></a>预览资源
预览你的资源，可查看图形资源，而无需打开它们。 预览功能也很有用的可执行文件后，已编译它们，因为资源标识符更改为数字。 这些数字标识符通常不提供足够的信息，因为预览资源可帮助快速识别它们。  
  
 您可以预览的可视布局部分的以下资源类型：  
  
-   Bitmap  
  
-   对话框  
  
-   图标  
  
-   菜单  
  
-   Cursor  
  
-   Toolbar  
  
 可视预览功能不适用于加速器、 清单、 字符串表和版本信息资源。  
  
### <a name="to-preview-resources"></a>若要预览资源  
  
1.  在中[资源视图](../windows/resource-view-window.md)或文档窗口中，选择你的资源，例如，IDD_ABOUTBOX。  
  
     **注意：** 如果你的项目尚未包含 .rc 文件，请参阅 [创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
2.  在中[属性窗口](/visualstudio/ide/reference/properties-window)，单击**属性页**按钮。  
  
     \- 或 -  
  
3.  上**视图**菜单上，单击**属性页**。  
  
     资源的属性页将打开，显示该资源的预览。 然后，您可以使用向上和向下箭头键导航资源视图或文档窗口中的树控件。 属性页将保持打开状态，并显示具有焦点并且能够预览的任何资源。  
  
 有关将资源添加到托管项目的信息，请参阅[桌面应用中的资源](/dotnet/framework/resources/index)中 *.NET Framework 开发人员指南*。 有关手动将资源文件添加到托管项目、 访问资源、 显示静态资源和将资源字符串分配给属性的信息，请参阅[桌面应用中创建资源文件](/dotnet/framework/resources/creating-resource-files-for-desktop-apps)。 全球化和本地化的托管应用中的资源的信息，请参阅[Globalizing and Localizing.NET Framework Applications](/dotnet/standard/globalization-localization/index)。  
  
## <a name="requirements"></a>要求 
  
 Win32  
  
## <a name="see-also"></a>请参阅  
 [如何：在项目外打开资源脚本文件（独立）](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)  
 [资源编辑器](../windows/resource-editors.md)