---
title: "GetProjectPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProjectPath"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProjectPath 方法"
ms.assetid: a5e51fe4-c068-47b7-9f2f-1a1d6c71a963
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetProjectPath
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回项目的目录路径。  
  
## 语法  
  
```  
  
      function GetProjectPath(   
   oProj    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目  
  
## 返回值  
 项目的目录路径。  
  
## 备注  
 调用此函数以获取项目的路径。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetProjectFile](../ide/getprojectfile.md)