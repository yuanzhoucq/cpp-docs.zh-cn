---
title: "检查基本向导项目 | Microsoft Docs"
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
  - "自定义向导, 创建的文件"
  - "自定义向导, 向导项目"
ms.assetid: c6423e3c-ddb0-43e0-b8e5-9e3a98a7908c
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 检查基本向导项目
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用[自定义向导](../ide/creating-a-custom-wizard.md)创建了基本项目后，检查向导所创建的文件。  
  
1.  在**解决方案资源管理器**中，展开项目并检查向导为项目创建的[文件](../ide/files-created-for-your-wizard.md)。  
  
2.  双击 Default.js 在代码编辑器中打开项目的 [JScript 文件](../ide/jscript-file.md)。  此文件包含 JScript 函数，该函数在用户单击向导中的“完成”时创建项目。  查看此文件中的函数和 TODO 注释。  
  
3.  如果项目具有用户界面，则查找标记为 [HTML 文件](../ide/html-files.md)的文件夹，并注意您具有的 .htm 文件与您在“自定义向导”的[应用程序设置](../ide/application-settings-custom-wizard.md)页中指定的一样多。  双击 Default.htm 在 [HTML 设计器](../Topic/HTML%20Designer.md)中打开项目的主 HTML 页。  可以在[Design View](../Topic/Design%20View1.md)或 HTML 视图中查看 HTML，就像查看 [HTML 标记](http://msdn.microsoft.com/zh-cn/7bb90672-b36a-4cf9-9bbc-677c9b956318)一样。  切换到“HTML 标记视图”并查看 HTML 标记。  单击“仅显示脚本视图”按钮（位于“HTML 视图”编辑窗口的右上角和“事件”下拉列表的旁边）并查看 .htm 文件中的 JScript。  默认情况下，此文件包含初始化和加载向导的 JScript 函数并提供 **IVCWizCtrlUI** 接口的默认行为。  有关更多信息，请参见 coclass <xref:Microsoft.VisualStudio.VsWizard.VCWizCtl> 对象。  
  
4.  保存并关闭向导项目。  
  
5.  打开 Visual Studio**“新建项目”**对话框，并找到向导图标。  双击该图标以显示向导。  可以查看“自定义向导”为您创建的基本向导页。  注意，第一页包含一些示例 HTML 控件和标准“完成”、“取消”和“帮助”按钮。  
  
6.  单击“完成”用向导生成新项目。  默认情况下，向导会创建两个文本文件：ReadMe.txt 和 Sample.txt。  这些文件描述向导所创建的项目。  关闭此项目并重新打开向导项目。  
  
7.  阅读[检查向导的机制](../ide/examining-the-mechanics-of-a-wizard.md)，对 Visual Studio 环境和 Visual C\+\+ 向导引擎如何创建您在运行向导时创建的项目有一个更清楚的了解。  
  
 准备开始[自定义您的自定义向导](../ide/customizing-your-wizard.md)。  
  
## 请参阅  
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [向导的设计步骤](../ide/steps-to-designing-a-wizard.md)   
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [提供区分上下文的帮助](../ide/providing-context-sensitive-help.md)   
 [自定义向导](../ide/customizing-your-wizard.md)