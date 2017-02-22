---
title: "Viewing and Editing Resources in a Resource Editor | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.resourceview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "resources [Visual Studio], viewing"
  - "rc files, viewing resources"
  - "Resource View pane"
  - "layouts, previewing resource"
  - "code, viewing resources"
  - "resource editors, viewing resources"
  - ".rc files, viewing resources"
  - "resources [Visual Studio], editing"
ms.assetid: ba8bdc07-3f60-43c7-aa5c-d5dd11f0966e
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# Viewing and Editing Resources in a Resource Editor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每种资源类型都具有专用的资源编辑器。  可以使用关联的编辑器对资源进行重新排列、调整大小、添加控件和功能或以其他方式修改资源的各方面。  还可以编辑[文本格式](../windows/how-to-open-a-resource-script-file-in-text-format.md)和[二进制格式](../mfc/opening-a-resource-for-binary-editing.md)的资源。  
  
 有些资源类型是可以以各种方式导入和使用的单个文件；这些资源包括位图、图标、光标、工具栏和 html 文件。  这类资源具有文件名和[资源标识符](../mfc/symbols-resource-identifiers.md)。  其他资源（如 Win32 项目中的对话框、菜单和字符串表）则仅作为资源脚本 \(.rc\) 文件或资源模板 \(.rct\) 文件的一部分存在。  
  
> [!NOTE]
>  资源的属性[可以使用“属性”窗口进行修改](../windows/changing-the-properties-of-a-resource.md)。  
  
## Win32 资源  
 可以在[资源视图](../windows/resource-view-window.md)窗格中访问 Win32 资源。  
  
#### 在资源编辑器中查看 Win32 资源  
  
1.  从**“视图”**菜单中选择**“资源视图”**。  
  
2.  如果“资源视图”窗口不是最顶层的窗口，则单击“资源视图”选项卡将它放到顶层。  
  
3.  在“资源视图”中，展开包含要查看的资源的项目的文件夹。  例如，如果希望查看对话框资源，则展开“对话框”文件夹。  
  
    > [!NOTE]
    >  如果您的项目尚未包含 .rc 文件，请参见[创建新资源脚本文件](../windows/how-to-create-a-resource-script-file.md)。  
  
4.  双击资源，如 IDD\_ABOUTBOX。  
  
     资源在适当的编辑器中打开。  例如，对于对话框资源，资源在对话框编辑器内打开。  
  
     还可以[在不打开项目的情况下查看 .rc（资源脚本）文件中的资源](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
#### 删除现有的 Win 32 资源  
  
1.  在“资源视图”中展开某种资源类型的节点。  
  
2.  在要删除的资源上右击并从快捷菜单中选择“删除”。  
  
    > [!NOTE]
    >  当从项目外在文档窗口中打开 .rc 文件时，可以使用同一快捷菜单命令删除某个资源。  
  
## 托管项目中的资源  
 由于托管项目不使用资源脚本文件，因此您必须从**解决方案资源管理器**打开资源。  您可以使用[图像编辑器](../mfc/image-editor-for-icons.md)和[二进制编辑器](../mfc/binary-editor.md)来与托管项目中的资源文件一起使用。  您要编辑的任何托管资源都必须是链接的资源。  Visual Studio 资源编辑器不支持编辑嵌入的资源。  
  
 有关将资源添加到托管项目的信息，请参见“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。有关手动将资源文件添加到托管项目、访问资源、显示静态资源和将资源字符串分配给属性的信息，请参见[演练：本地化 Windows 窗体](http://msdn.microsoft.com/zh-cn/9a96220d-a19b-4de0-9f48-01e5d82679e5)和[Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md)。  
  
#### 在资源编辑器中查看托管资源  
  
1.  在解决方案资源管理器中，右击资源，如 Bitmap1.bmp。  
  
     资源在适当的编辑器中打开。  
  
#### 删除现有托管资源  
  
1.  在解决方案资源管理器中，右击要删除的资源并在快捷菜单中选择“删除”。  
  
### 要求  
 无  
  
## 请参阅  
 [Resource Editors](../mfc/resource-editors.md)