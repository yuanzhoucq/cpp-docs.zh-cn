---
title: "RenderAddTemplate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "RenderAddTemplate"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RenderAddTemplate 方法"
ms.assetid: 84c898d6-8676-4ae1-9245-c023e1c9ab92
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# RenderAddTemplate
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

呈现模板文件，还可以将其添加到项目中。  
  
## 语法  
  
```  
  
      function RenderAddTemplate(   
   strTemplateFile,   
   strProjectFile,   
   ProjToAddTo,   
   bOpen    
);  
```  
  
#### 参数  
 *strTemplateFile*  
 只是模板文件名（不包括路径），相对于 TEMPLATES\_PATH。  
  
 *strProjectFile*  
 所创建的新文件的名称。  该字符串可以包含路径，但相对于 PROJECT\_PATH。  
  
 *ProjToAddTo*  
 项目对象。  如果所创建的文件必须添加到项目，则提供项目名称；否则，如果不希望将文件添加到项目，则忽略它或传递 **false**。  
  
 *bOpen*  
 如果为 **true**，则将文件添加到项目后，在默认编辑器中打开该文件。  
  
## 备注  
 调用该函数以呈现模板文件并可选择是否将其添加到项目。  
  
## 示例  
  
```  
// Declare the project path and the template path.  
var strProjectPath = wizard.FindSymbol("PROJECT_PATH");  
var strTemplatePath = wizard.FindSymbol("TEMPLATES_PATH");  
// Declare the template header and implementation files.  
var strTemplateHeader = wizard.FindSymbol("TEMPLATE_HEADER");  
var strTemplateImpl = wizard.FindSymbol("TEMPLATE_IMPL");  
// Render the template strTemplateHeader and open it in the editor.  
RenderAddTemplate(strTemplateHeader, strHeaderFile, selProj, true);   
// Render the template strTemplateImpl, but do not open it   
// in the editor.  
RenderAddTemplate(strTemplateImpl, strImplFile, selProj, false);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)