---
title: "自定义向导 | Microsoft Docs"
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
  - "自定义向导"
  - "自定义向导, 在 Visual C++ 项目中创建"
ms.assetid: a3ff1c81-3eef-41e7-a6bc-2f98e4bf423f
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 自定义向导
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

在自定义用[自定义向导](../ide/application-settings-custom-wizard.md)创建的向导时，必须考虑以下常规任务。  
  
-   在 .vsz 文件中，指定使向导工作所必需的任何自定义参数。  有关更多信息，请参见 [.vsz 文件（项目控件）](../ide/dot-vsz-file-project-control.md)和[预定义自定义向导符号](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)。  
  
     如果将向导本地化为若干不同的语言，请将这些语言参数添加到 .vsz 文件中。  有关更多信息，请参见[将向导本地化为多种语言](../ide/localizing-a-wizard-to-multiple-languages.md)。  
  
-   自定义[模板文件](../ide/template-files.md)（和 [Templates.inf](../ide/templates-inf-file.md)）以便为用户选择指定指令。  
  
-   自定义 [Default.js 文件](../ide/jscript-file.md)以便为向导指定其他特殊处理。  可以编写自己的函数，也可以使用 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md) 提供的函数。  
  
-   设计 HTML 用户界面将使用的图标和其他图像。  
  
-   设计 HTML 用户界面。  
  
-   将符号添加到 HTML 符号表以匹配按钮、控件、文本框和向导使用的其他元素。  
  
     下面显示“自定义向导”提供的一段 HTML 摘录：  
  
    ```  
    <SYMBOL NAME="WIZARD_DIALOG_TITLE" TYPE=text VALUE="MyCustomWiz">  
          </SYMBOL>  
    <SYMBOL NAME="SAMPLE_CHECKBOX" TYPE=checkbox VALUE=true>  
          </SYMBOL>  
    ```  
  
     此向导（标题为 MyCustomWiz）显示一个在默认情况下选中的复选框。  
  
-   在 HTML 文件中标记为 `<SCRIPT LANGUAGE="JSCRIPT">` 的节中添加 JScript 函数调用，并访问 Visual Studio 对象模型以自定义向导的行为。  必须使用 `window.external` 调用这些函数，如下所示：  
  
    ```  
    window.external.AddSymbol("MAIN_FRAME_DEFAULT_STYLES", true);  
    window.external.AddSymbol("MAIN_FRAME_STYLE_FLAGS", "");  
    ```  
  
    > [!NOTE]
    >  利用通过 [Visual Studio 的自动化和扩展性](../Topic/Automation%20and%20Extensibility%20for%20Visual%20Studio.md)、[Visual C\+\+ 代码模型](http://msdn.microsoft.com/zh-cn/dd6452c2-1054-44a1-b0eb-639a94a1216b)、[项目模型](http://msdn.microsoft.com/zh-cn/06c1bbd9-4c79-4f97-ad6d-2b1dea8ecd1f)和[向导模型](http://msdn.microsoft.com/zh-cn/159395ac-33c7-47bf-ad42-4e1435ddc758)公开的方法、属性和事件，您可以在 JScript 文件和 .htm 文件中以编程方式管理向导项目的所有方面（从创建到生成）。  
  
-   如有必要，自定义 [.vsdir 文件](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)，使 shell 能够理解有关 .vsz 文件和所有其他模板的信息。  例如，指示图标资源 ID、标志、本地化名称等等。  
  
-   用向导需要本地化为的所有语言创建 .htm 文件和模板文件。  然后将它们添加到适当的项目目录中。  
  
-   为向导[提供区分上下文帮助](../ide/providing-context-sensitive-help.md)。  
  
## 请参阅  
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [向导的设计步骤](../ide/steps-to-designing-a-wizard.md)   
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [提供区分上下文的帮助](../ide/providing-context-sensitive-help.md)   
 [在向导中处理错误](../ide/handling-errors-in-wizards.md)