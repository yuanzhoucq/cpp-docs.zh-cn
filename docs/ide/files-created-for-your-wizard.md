---
title: "为向导创建的文件 | Microsoft Docs"
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
  - "自定义向导, 删除文件"
  - "自定义向导, 创建的文件"
  - "文件 [C++], “自定义向导”创建的"
  - "图标, 删除"
ms.assetid: 7f0e393c-395e-491b-add2-904cf8838e81
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# 为向导创建的文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

向导使用在**“新建项目”**对话框的**“名称”**框中指定的名称派生某些文件和类的名称。  
  
 [自定义向导](../ide/custom-wizard.md)将注释添加到为向导创建的文件中。  “自定义向导”还在新应用程序目录中创建文本文件 readme.txt。  该文件阐释由“自定义向导”创建的其他新文件的内容和用法。  
  
 下表描述由“自定义向导”创建的文件。  有关主要元素如何交互以创建向导的更多信息，请参见[设计向导](../ide/designing-a-wizard.md)。  
  
|文件|说明|  
|--------|--------|  
|[Project.vsz](../ide/dot-vsz-file-project-control.md)|与旧 .ini 格式类似的文本文件。  它标识向导引擎并提供上下文和可选的[自定义参数](../ide/custom-parameters-in-the-wizard-dot-vsz-file.md)。|  
|[Project.vsdir](../Topic/Adding%20Wizards%20to%20the%20Add%20Item%20and%20New%20Project%20Dialog%20Boxes%20by%20Using%20.Vsdir%20Files.md)|一个文本文件，它使 Visual Studio shell 可查找向导并将其显示在**“新建项目”**对话框中。|  
|[HTML 文件（可选）](../ide/html-files.md)|向导可以包含用户界面 \(UI\)，即 HTML 界面。  没有 UI 的向导不包含任何 HTML 文件。<br /><br /> 如果向导具有 UI，则该向导中的每个屏幕称作一“页”，每页都会指定 UI 功能。<br /><br /> default.htm 文件定义向导中的第一页。  使用[“自定义向导”\-\>“应用程序设置”](../ide/application-settings-custom-wizard.md)的**“页数”**列表框，可以指定附加页。  每个附加页由 Page\_*page\-number*.htm 文件定义，其中 *page\-number* 的范围为 2 到您指定的页数。|  
|[脚本文件](../ide/jscript-file.md)|“自定义向导”为每个创建的向导创建 JScript 文件 default.js。  该文件包含访问 Visual C\+\+ 向导、代码和环境对象模型以自定义向导的 JScript 函数。  可以在向导的 default.js 文件中自定义和添加这些函数。<br /><br /> 另外，向导还包括 [common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md) 文件，该文件包含常用的 JScript 函数并在所有向导（包括 Visual C\+\+ 用来创建其他项目类型的向导）间共享。  有关更多信息，请参见[用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)。|  
|[模板](../ide/template-files.md)|向导模板是包含指令的文本文件的集合，这些指令根据向导用户的选择被分析并插入符号表中。  模板文本文件根据用户输入呈现并添加到由向导创建的项目中。  获取适当信息的方法是直接访问向导控件的符号表。|  
|[Templates.inf](../ide/templates-inf-file.md)|文本文件，列出与项目关联的所有模板。|  
|Default.vcxproj|.xml 文件，包含有关项目类型的信息。|  
|Sample.txt|模板文件，显示如何使用向导指令。|  
|ReadMe.txt|模板文件，包含“自定义向导”所创建的每个文件的摘要。|  
|Images（可选）|可以提供任何图像（如图标、GIF、BMP 和 HTML 支持的其他图像格式）增强向导的 UI。  没有 UI 的向导不需要图像。|  
|Styles.css（可选）|定义 UI 样式的文件。  如果向导没有用户界面，则“自定义向导”不创建 .css 文件。|  
  
 如果删除向导文件和目录，还必须从 \\vc7\\vcprojects\\ 目录中删除下列文件。  在删除这些文件之前，向导图标将继续出现在**新建项目**对话框中。  
  
-   *projectname*.vsz  
  
-   *projectname*.ico  
  
-   *projectname*.vsdir  
  
## 请参阅  
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)