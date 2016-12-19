---
title: "检查向导的机制 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
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
  - "自定义向导, 向导项目"
ms.assetid: 79917075-a843-40f6-abf8-64d98e5f6bdc
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 检查向导的机制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

不必编译向导项目即可让用户立即开始使用它。  创建了必要的元素后，VSDIR 会指示`New Project`对话框显示向导图标，并指示`Add New Item`对话框在快捷菜单中显示向导名称。  用户通过选择向导名称可以立即启动向导。  
  
 当用户启动向导时，环境 shell 共同创建向导引擎并查询 <xref:EnvDTE.IDTWizard>。  然后，它调用 <xref:EnvDTE.IDTWizard.Execute%2A> 以启动向导。  
  
> [!NOTE]
>  如果向导没有界面，则项目以所提供的默认设置创建并显示在解决方案资源管理器中，具有 .vsz 文件中提供的节点结构。  本主题的其余部分假定向导具有 UI。  
  
 如果向导具有 UI，则用户接受或更改向导基于 HTML 的 UI 中每个控件的默认值。  当用户在向导页中浏览并进行更改时，在 HTML 的“脚本”节中会调用 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.Navigate%2A> 和 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.Next%2A> 等函数。  
  
 每当用户在向导内选择不同的选项时，向导控件的符号表中会捕获这些选择。  符号表与向导 HTML 页中的控件的 ID 匹配，以维护用户选择与符号表之间的一一对应。  
  
 当用户在向导 UI 中单击**“完成”**时，将从 HTML 脚本调用 JScript 函数“OnFinish”。  
  
> [!NOTE]
>  可以在 Default.js 中自定义“OnFinish”以执行所需的任何其他任务。  
  
 然后，向导引擎扫描模板文件，并基于用户选择分析和呈现文件。  它将呈现的文件复制到项目目录并将这些文件添加到项目中。  新创建的项目加载在 Visual Studio 环境中，而项目的节点和文件显示在解决方案资源管理器中。  
  
## 请参阅  
 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl>   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [向导的设计步骤](../ide/steps-to-designing-a-wizard.md)   
 [自定义向导](../ide/customizing-your-wizard.md)