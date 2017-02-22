---
title: "CreateProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CreateProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateProject 方法"
ms.assetid: b5598b46-fe29-4ad0-8bfe-a4dc789aeebd
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CreateProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建 C\+\+ 项目。  
  
## 语法  
  
```  
  
      function CreateProject(   
   strProjectName,   
   strProjectPath    
);  
```  
  
#### 参数  
 `strProjectName`  
 包含项目名称的字符串。  
  
 *strProjectPath*  
 包含项目路径的字符串。  
  
## 返回值  
 项目对象。  
  
## 备注  
 调用该函数以创建可在 Visual Studio 中打开的 C\+\+ 项目。  如果将向导的上下文参数 **WizardType** 指定为 **vsWizardAddSubProject**，则项目作为子项目添加到现有项目。  有关更多信息，请参见 [ContextParams 枚举](../Topic/Context%20Parameters%20for%20Launching%20Wizards.md)。  
  
## 示例  
 请参见 [AddFilesToProject](../ide/addfilestoproject.md)。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)