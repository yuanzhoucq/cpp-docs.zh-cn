---
title: "自动化模型 | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "自动化 [Visual Studio SDK], 自动化模型"
ms.assetid: 48ddc192-96ff-46dc-a1fe-df4eb5c62c84
caps.latest.revision: 16
caps.handback.revision: 16
manager: "douge"
---
# 自动化模型
自动化模型提供 VSPackage 替代选项，以扩展 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)]。 自动化模型在早期的 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 版本中被称为扩展性模型，它现在是一个编程接口，使你可以访问驱动集成开发环境 \(IDE\) 的基础例程，并允许进行自定义、调整和自动化。  
  
## Vspackage 和自动化  
 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK 文档重点介绍 Vspackage，它的开发潜力比自动化模型大。 例如，可以针对自动化模型中的对象编写代码，从而自定义一种语言，如 [!INCLUDE[vbprvb](../Token/vbprvb_md.md)]。 但是，不能使用自动化模型向 IDE 添加新语言。 若要向该环境添加新语言，必须开发 VSPackage。  
  
 自动化模型和 VSPackage 模型两者一起构成了一种双管齐下的方法，在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中实现了可扩展性。 可扩展性是增强和扩展 IDE 功能的能力。 自动化是指用户创建的代码和工具，它们可以在现有环境中自动化任务，并以编程方式驱动 IDE。 而 Vspackage 则允许你向 IDE 添加新功能。 VSPackage 是可共同创建的对象，即它有类工厂且可以通过实现 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage> 接口使其可供 IDE 使用。  
  
 加载项和向导通过使用自动化模型及其接口来控制和扩展 IDE 的功能。 通常情况下，Microsoft 提供许多具有 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 的加载项。 可以使用加载项来将新的命令集成到工具栏和菜单上、添加工具窗口，或者自动执行某些在 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 中定期完成的任务。  
  
 作为 VSPackage 开发人员，你应该参与自动化模型的开发。 例如，如果你通过使用 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] SDK 向 [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] 添加一种新语言，那么该语言应提供一个可靠的代码模型来扩展现有的代码。 有关详细信息，请参阅[导致自动化模型](../Topic/Contributing%20to%20the%20Automation%20Model.md)。  
  
## 请参阅  
 [Vspackage](../Topic/VSPackages.md)   
 [导致自动化模型](../Topic/Contributing%20to%20the%20Automation%20Model.md)