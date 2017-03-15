---
title: "SetFilters | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetFilters"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetFilters 方法"
ms.assetid: ae934e1b-8ead-4c1d-a0f8-e9c80d182340
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SetFilters
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为项目文件夹添加源、包含和资源筛选器。  
  
## 语法  
  
```  
  
      function SetFilters(   
   oProj    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
## 备注  
 调用该函数为项目文件夹添加源、包含和资源筛选器。  该函数在项目中查找以下符号：  
  
-   SOURCE\_FILTER  
  
-   INCLUDE\_FILTER  
  
-   RESOURCE\_FILTER  
  
 这些符号包含筛选中所使用的文件扩展名。  
  
## 示例  
  
```  
// Create and set the project name and path.  
selProj = CreateProject(strProjectName, strProjectPath);  
// Add the previously-identified configurations to the project.  
AddConfigurations(selProj, strProjectName);  
// Set filters for the project.  
SetFilters (selproj);  
// Indicate that the project is an ATL project.  
selProj.Object.keyword = "AtlProj";  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)