---
title: "向导的设计步骤 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "自定义向导, 设计"
ms.assetid: dc22746b-99e3-4569-a8b4-b3d7cbabf8f2
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 向导的设计步骤
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

可以使用向导创建和配置通用的项目起始文件。  与任何项目一样，创建向导需要进行规划。  下列步骤描述一种使您熟悉 Visual C\+\+“自定义向导”并将其应用到自己项目中的方法。  
  
1.  检查 Visual Studio 中包含的[自定义向导示例](http://msdn.microsoft.com/zh-cn/6afa2143-062c-4a68-81ca-66cbf4b95261)。  
  
2.  为向导应创建的项目类型奠定基础。  与构造所有应用程序一样，此过程可经过许多实际操作和许多不同的反复试验。  
  
3.  使用 Visual C\+\+ [自定义向导](../ide/creating-a-custom-wizard.md)创建项目，并指定用户界面和页码选项。  
  
    > [!NOTE]
    >  如果不指定用户界面（即如果清除“自定义向导”的[“自定义向导”\-\>“应用程序设置”](../ide/application-settings-custom-wizard.md)中的“用户界面”），向导会将自定义参数 WIZARD\_UI 设置为 **FALSE**，并创建没有用户输入和 .htm 文件的项目模板文件。  因此不必指定页码。  有关更多信息，请参见 [.vsz 文件（项目控件）](../ide/dot-vsz-file-project-control.md)。  
  
4.  [检查基本项目](../ide/examining-the-basic-wizard-project.md)，它是由“自定义向导”创建的。  
  
5.  如果向导具有用户界面，运行该向导以[进一步了解自定义向导的机制](../ide/examining-the-mechanics-of-a-wizard.md)。  
  
6.  [自定义基本向导](../ide/customizing-your-wizard.md)。  
  
7.  [提供区分上下文的帮助](../ide/providing-context-sensitive-help.md)。  
  
8.  为 JScript 和 HTML 代码[提供错误处理](../ide/handling-errors-in-wizards.md)。  
  
9. 生成并测试向导。  
  
10. 调试向导。  有关更多信息，请参见[调试脚本和 Web 应用程序](../Topic/Debugging%20Web%20Applications%20and%20Script.md)。  
  
    > [!NOTE]
    >  调试 JScript 时，不能对本机代码执行混合模式的调试。  
  
## 请参阅  
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)