---
title: "“添加资源”对话框 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.insertresource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "资源 [Visual Studio]，添加"
  - "“添加资源”对话框"
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# “添加资源”对话框
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用此对话框将资源添加到 C\+\+ Windows 桌面应用程序项目。  
  
> [!NOTE]
>  此信息不适用于 Windows 应用商店应用中的资源。 有关的详细信息，请参阅[定义应用资源](http://msdn.microsoft.com/zh-cn/476ea844-632c-4467-9ce3-966be1350dd4)。  
  
 **资源类型**  
 指定你想要创建的资源类型。  
  
 你可以展开光标和对话框资源目录以显示其他资源。 这些资源位于 ...\\Microsoft Visual Studio `version`\\VC\\VCResourceTemplates\\\<LCID\>\\mfc.rct 中。 如果添加 .rct 文件，则必须将这些文件放在此目录中或为其指定[包含路径](../windows/how-to-specify-include-directories-for-resources.md)。 之后，这些文件中的资源将显示在相应类别下的第二层。 可添加的 .rct 文件数没有预设限制。  
  
 显示在树控件顶层的资源是 Visual Studio 提供的默认资源。  
  
 **新建**  
 根据你在“资源类型”框中选定的类型来创建资源。 资源将在适当的编辑器中打开。 例如，如果创建对话框资源，则它将在[对话编辑器](../mfc/dialog-editor.md)中打开。  
  
 **导入**  
 打开“导入”对话框，可在此对话框中导航到要导入当前项目中的资源。 可导入位图、图标、光标、HTML 资源文件、声音 \(.WAV\) 资源文件或自定义资源文件。  
  
 **自定义**  
 打开[“新建自定义资源”对话框](../windows/new-custom-resource-dialog-box.md)，可在其中创建自定义资源。 仅可以在二进制编辑器中编辑自定义资源。  
  
## 要求  
 无  
  
## 请参阅  
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)