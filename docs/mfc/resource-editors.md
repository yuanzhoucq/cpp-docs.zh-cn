---
title: "Resource Editors | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.editors.resource"
  - "vc.resvw.resource.editors"
  - "vs.resvw.resource.editors"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "editors [C++], resource"
  - "editors [C++]"
  - "resource editors"
  - "Windows [C++], application resource editing"
ms.assetid: e20a29ec-d6fb-4ead-98f3-431a0e23aaaf
caps.latest.revision: 16
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Resource Editors
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

资源编辑器是用于创建或修改 Visual Studio 项目中所含资源的专用环境。 Visual Studio 资源编辑器共享技术和接口，以帮助你快速、轻松地创建和修改应用程序资源。 通过资源编辑器，你可以[在适当的编辑器中查看和编辑资源](../mfc/viewing-and-editing-resources-in-a-resource-editor.md)并[预览资源](../mfc/previewing-resources.md)。  
  
 创建或打开某个资源时，将自动打开相应的编辑器。  
  
 **注意** 由于托管的项目不使用资源脚本文件，因此你必须从“解决方案资源管理器”打开资源。 你可以使用[图像编辑器和](../mfc/image-editor-for-icons.md)[二进制编辑器](../mfc/binary-editor.md)处理托管项目中的资源文件。 你要编辑的任何托管资源都必须是链接的资源。 Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”[](../Topic/Resources%20in%20Desktop%20Apps.md)中的*应用程序中的资源*。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参阅[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和 [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
|使用...|编辑...|  
|-----------|-----------|  
|[快捷键编辑器](../mfc/accelerator-editor.md)|Visual C\+\+ 项目中的快捷键对应表。|  
|[二进制编辑器](../mfc/binary-editor.md)|二进制数据信息和 Visual C\+\+、Visual Basic 或 Visual C\# 项目中的自定义资源。|  
|[对话框编辑器](../mfc/dialog-editor.md)|Visual C\+\+ 项目中的对话框。|  
|[HTML 设计器](../Topic/HTML%20Designer.md)|设计视图和 HTML 视图中的 HTML 页面。 警告：你无法对位于 EXE 或 DLL 中的 HTML 页面进行更改，因为所做的更改不导回 EXE 或 DLL 中。|  
|[图像编辑器](../mfc/image-editor-for-icons.md)|Visual C\+\+、Visual Basic 或 Visual C\# 项目中的位图、图标、光标以及其他图像文件。|  
|[菜单编辑器](../mfc/menu-editor.md)|Visual C\+\+ 项目中的菜单资源。|  
|[Ribbon 编辑器](../mfc/ribbon-designer-mfc.md)|MFC 项目中的功能区资源。|  
|[字符串编辑器](../mfc/string-editor.md)|Visual C\+\+ 项目中的字符串表。|  
|[工具栏编辑器](../mfc/toolbar-editor.md)|Visual C\+\+ 项目中的工具栏资源。 工具栏编辑器是图像编辑器的一部分。|  
|[版本信息编辑器](../mfc/version-information-editor.md)|Visual C\+\+ 项目中的版本信息。|  
  
## 要求  
 无  
  
## 请参阅  
 [Working with Resource Files](../mfc/working-with-resource-files.md)   
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Symbols: Resource Identifiers](../mfc/symbols-resource-identifiers.md)   
 [菜单和其他资源](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)