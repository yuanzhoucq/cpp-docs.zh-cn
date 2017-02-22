---
title: "JScript 文件 | Microsoft Docs"
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
  - "AddConfig 方法"
  - "AddFilesToCustomProj 方法"
  - "AddFilters 方法"
  - "Common.js 文件"
  - "CreateCustomInfFile 方法"
  - "CreateCustomProject 方法"
  - "自定义向导, 访问向导对象模型"
  - "自定义向导, JScript 文件"
  - "调试 [JScript], 启用脚本调试"
  - "调试 [JScript], JScript 文件"
  - "调试脚本"
  - "调试脚本, 启用脚本调试"
  - "Default.js 文件"
  - "DelFile 方法"
  - "文件 [C++], “自定义向导”创建的"
  - "GetTargetName 方法"
  - "JScript 文件"
  - "OnFinish 方法"
  - "PchSettings 方法"
ms.assetid: 7841a09e-2dd2-4f1a-a13a-39ac53f24315
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# JScript 文件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[自定义向导](../ide/custom-wizard.md)访问脚本引擎并为每个项目创建一个称为 Default.js 的 JScript 文件。  它还包括 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)。  这些文件包含使您可以访问 Visual Studio 和 Visual C\+\+ 对象模型以自定义向导的 JScript 函数。  （有关这些模型的列表，请参见[设计向导](../ide/designing-a-wizard.md)。）可将自己的函数添加到向导项目的 Default.js 文件中。  若要从 JScript 文件访问向导对象模型或环境模型中的属性和方法，请分别用“wizard.”和“dte.”前置对象模型项。  
  
 例如：  
  
```  
function CreateCustomProject(strProjectName, strProjectPath)  
{  
   try  
   {  
      var strProjTemplatePath = wizard.FindSymbol('PROJECT_TEMPLATE_PATH');  
var strProjTemplate = '';  
      strProjTemplate = strProjTemplatePath + '\\default.vcproj';  
  
      var Solution = dte.Solution;  
      var strSolutionName = "";  
      if (wizard.FindSymbol("CLOSE_SOLUTION"))  
...  
```  
  
 当在[自定义向导](../ide/custom-wizard.md)中单击“完成”时，向导将在解决方案资源管理器的 Script Files 文件夹中加载 Default.js 文件。  此 JScript 文件创建项目并呈现模板，然后在用户单击向导中的“完成”时将它们添加到解决方案中。  
  
 默认情况下，项目的 Default.js 文件包含以下函数：  
  
|函数名|说明|  
|---------|--------|  
|**AddConfig**|添加项目的配置。  可以提供编译器和链接器设置。|  
|**AddFilesToCustomProj**|当用户单击“完成”时，将指定的文件添加到项目中。|  
|**AddFilters**|当用户单击“完成”时，将指定的源筛选器添加到项目中。|  
|**CreateCustomProject**|当用户单击“完成”时，在指定位置创建项目。|  
|**CreateCustomInfFile**|创建项目的 [Templates.inf 文件](../ide/templates-inf-file.md)。|  
|**DelFile**|删除指定的文件。|  
|**GetTargetName**|获取指定文件的名称。|  
|**OnFinish**|当用户单击“完成”时，由向导调用以创建项目、添加文件和筛选器、呈现模板以及设置配置。|  
|**PchSettings**|设置预编译头设置。  有关更多信息，请参见 Common.js 参考中的 [SetCommonPchSettings](../ide/setcommonpchsettings.md)。|  
  
 每个向导均具有唯一的 Default.js 文件，该文件包括的 TODO 注释可帮助您识别必须自定义文件的地方。  
  
 Visual C\+\+ 还包括 [Common.js](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)，该文件在所有向导中共享并包含在向导项目中。  可以使用 Common.js 中的函数。  
  
> [!NOTE]
>  Common.js 包含每个函数及其参数的说明。  有关更多信息，请参见 Common.js 中的注释。  
  
 如果具有要在向导项目之间共享的函数，则可将它们添加到 Common.js 中。  创建您自己的 Common.js 版本并将其保存在公共路径中，然后在 [.vsz 文件](../ide/dot-vsz-file-project-control.md)中将 SCRIPT\_COMMON\_PATH 设置为此路径。  
  
> [!NOTE]
>  随 Visual C\+\+ 提供的向导使用 Common.js 中的 JScript 函数。  如果更改这些函数，Visual C\+\+ 向导的行为可能会出现异常。  
  
 有关 JScript 的更多信息，请参见 [Writing, Compiling, and Debugging JScript Code](http://msdn.microsoft.com/zh-cn/13e57e7d-4867-4555-b9e4-fc24aa75e628)。  
  
## 调试脚本  
 若要在向导 html 文件中调试脚本，必须启用脚本调试。  
  
#### 启用脚本调试  
  
1.  在 Internet Explorer 中，单击“工具”菜单并选择**“Internet 选项”**。  
  
2.  单击**“高级”**选项卡。  
  
3.  在“浏览”类别下，清除“禁止脚本调试”复选框。  
  
 当您单击向导上的“完成”按钮时，这还将允许 common.js 和 default.js 显示在**“运行文档”**窗口中。  
  
## 请参阅  
 [为向导创建的文件](../ide/files-created-for-your-wizard.md)   
 [自定义向导](../ide/custom-wizard.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)