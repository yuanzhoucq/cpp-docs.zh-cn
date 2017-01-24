---
title: "设计向导 | Microsoft Docs"
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
  - "自定义向导 [C++], 项目的设计"
  - "项目 [C++], 自定义向导"
  - "Visual C++ 项目, 自定义向导"
  - "向导 [C++], 自定义"
ms.assetid: a7c0be7e-9297-4fed-83e3-5645c896d56b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 设计向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可能需要创建具有标准化功能的项目，它们不同于 Visual C\+\+ 所提供的应用程序向导。  对于这样的任务，可以使用 Visual C\+\+ 向导结构，该结构是为实现简单的可扩展性和自定义而设计的。  可以使用 [Visual C\+\+ 自定义向导](../ide/creating-a-custom-wizard.md)创建向导。  创建向导后，可以配置它以生成项目所需要的起始文件。  
  
 Visual C\+\+ 向导是 HTML 控件。  它使用 Visual C\+\+ 向导引擎 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI>，该向导引擎提供 <xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI.NavigateToCommandHandler%2A>、<xref:Microsoft.VisualStudio.VsWizard.IVCWizCtlUI.OkCancelAlert%2A> 等常见的服务。  向导还使用脚本引擎，该引擎使向导得以理解 VBScript 和 [JScript .NET](http://msdn.microsoft.com/zh-cn/c7e636ee-c10f-45b1-85ec-fe2daca30bf5)。  
  
 向导结构允许在向导中直接访问以下对象模型，并从 JScript 或 HTML 文件中调用它们的方法、属性和事件。  （有关更多信息，请参见 [HTML 文件](../ide/html-files.md)和 [JScript 文件](../ide/jscript-file.md)中的示例。）  
  
-   [开发人员工具环境 \(DTE\) 对象模型](../Topic/Extending%20the%20Visual%20Studio%20Environment.md)  
  
-   [Visual C\+\+ 代码模型](http://msdn.microsoft.com/zh-cn/dd6452c2-1054-44a1-b0eb-639a94a1216b)  
  
-   [Visual C\+\+ 项目模型](http://msdn.microsoft.com/zh-cn/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f)  
  
-   [Visual C\+\+ 向导模型](http://msdn.microsoft.com/zh-cn/159395ac-33c7-47bf-ad42-4e1435ddc758)  
  
 有关向导设计中的每个元素的说明，请参见[为向导创建的文件](../ide/files-created-for-your-wizard.md)。  
  
## 请参阅  
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [向导的设计步骤](../ide/steps-to-designing-a-wizard.md)   
 [自定义向导](../ide/customizing-your-wizard.md)