---
title: "How to: Use Resource Templates | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "language-specific template files"
  - "resource templates"
  - "resources [Visual Studio], creating"
  - "rct files"
  - "templates, resource templates"
  - "resources [Visual Studio], templates"
  - ".rct files"
ms.assetid: bdfe7060-f98e-4859-8285-9c8570360e9d
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# How to: Use Resource Templates
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

资源模板是保存为 .rct 文件的自定义资源。  因此，可将资源模板视为创建其他资源的起点。  资源模板可节省开发其他资源或共享功能（如标准控件和其他重复元素）的资源组的时间。  例如，你可能希望在多个对话框中包含“帮助”按钮和公司徽标的图标。  若要快速做到这一点，可以新建一个对话框模板，并用徽标和“帮助”按钮对其进行自定义。  
  
 自定义资源模板后，必须将所做的更改保存在模板文件夹中（或 include 路径中指定的任何位置），以便新的资源模板显示在[添加资源对话框](../windows/add-resource-dialog-box.md)中的资源类型下。  然后，你可以根据需要像往常一样使用资源模板。  
  
> [!NOTE]
>  你可以将语言特定的模板文件放在主模板目录的子目录中。  例如，你可以将只含英文的模板文件放在 \\\<资源模板目录\>\\1033 中。  
  
### 若要创建资源模板  
  
1.  在**“解决方案资源管理器”**中，右键单击项目。  
  
2.  从快捷菜单选择 **“添加”**，然后单击**“添加新项”**。  
  
3.  在**“添加新项”**对话框中的**“模板:”**窗格中，选择 **“资源模板文件 \(.rct\)”**。  
  
4.  为你的新 .rct 文件提供名称和位置，然后单击**“打开”**。  
  
5.  新的 .rct 文件将被添加到项目中，并将显示在**“资源”**文件夹下的“解决方案资源管理器”中。  
  
     现在，双击 .rct 文件以在文档窗口中打开它，然后将资源添加到其中（右键单击文档窗口中的文件并从快捷菜单选择**“添加资源”**）。  这时，你便可以自定义这些资源并保存为 .rct 文件了。  
  
    > [!NOTE]
    >  在创建新的 RCT 文件时，Visual Studio 将在 \\Program Files\\Microsoft Visual Studio 9.0\\VC\\VCResourceTemplates、\\Program Files\\Microsoft Visual Studio 9.0\\VC\\VCResourceTemplates\\*LCID*（例如 1033 为英语），*或* [include 路径](../windows/how-to-specify-include-directories-for-resources.md)中的任何位置搜素该文件。  如果你想将 RCT 文件保存到另一个文件夹，例如 \\My Documents，则只需将此文件夹添加到 include 路径，Visual Studio 就会查找该 RCT 文件。  
  
### 若要将现有的 .rc 文件转换为 .rct 文件  
  
1.  [将 .rc 文件作为一个独立的文件打开](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)。  
  
2.  在**“文件”**菜单上，单击**“将 \<*你的文件名*\> 另存为”**。  
  
3.  指定一个位置，然后单击**“确定”**。  
  
### 若要从模板创建新资源  
  
1.  在[“资源视图”](../windows/resource-view-window.md)窗格中，右键单击 .rc 文件并从快捷菜单选择**“添加资源”**。  
  
2.  在**“添加资源”**对话框中，单击资源旁边的加号 \(**\+**\)，以展开资源节点并查看可用于该资源的所有模板。  
  
3.  双击要使用的模板。  
  
4.  根据需要在相应的资源编辑器中修改已添加的资源。  
  
     资源编辑器将自动提供一个唯一的资源 ID。  你可以根据需要修改[资源属性](../windows/changing-the-properties-of-a-resource.md)。  
  
 有关将资源添加到托管项目的信息，请参阅“.NET Framework 开发员指南”中的[应用程序中的资源](../Topic/Resources%20in%20Desktop%20Apps.md)。  
  
 要求  
  
 Win32  
  
## 请参阅  
 [Resource Files](../mfc/resource-files-visual-studio.md)   
 [Resource Editors](../mfc/resource-editors.md)