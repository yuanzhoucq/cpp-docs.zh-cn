---
title: "AddFilesToProject | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddFilesToProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddFilesToProject 方法"
ms.assetid: 3ff11406-bb4a-4eb7-a8df-c655b964ff76
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AddFilesToProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将 Templates.inf 中列出的所有文件添加到项目中。  
  
## 语法  
  
```  
  
      function AddFilesToProject(   
   oProj,   
   strProjectName,   
   InfFile    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
 `strProjectName`  
 项目的名称。  
  
 *InfFile*  
 Templates.inf 文件对象。  该文件包含向导在完成时创建的文件名列表。  
  
## 备注  
 调用该函数可将 Templates.inf 中列出的所有文件添加到项目中。  使用该函数可以添加模板文件、资源文件或帮助文件。  
  
## 示例  
  
```  
// Assign the project path and project name.  
var strProjectPath = wizard.FindSymbol("PROJECT_PATH");  
var strProjectName = wizard.FindSymbol("PROJECT_NAME");  
  
// Create the Visual C++ project and call it "MyProj"  
selProj = CreateProject(strProjectName, strProjectPath);  
selProj.Object.Keyword = "MyProj";  
  
// Add common and specific configurations to the project.  
AddCommonConfig(selProj, strProjectName);  
AddSpecificConfig(selProj, strProjectName);  
  
// Set the project filters  
SetFilters(selProj);  
  
// Create the project's Templates.inf file   
var InfFile = CreateInfFile();  
  
// Add the files in Templates.inf to the project.  
AddFilesToProject(selProj, strProjectName, InfFile);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [CreateInfFile](../ide/createinffile.md)   
 [SetCommonPchSettings](../ide/setcommonpchsettings.md)