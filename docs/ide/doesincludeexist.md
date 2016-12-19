---
title: "DoesIncludeExist | Microsoft Docs"
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
  - "DoesIncludeExist"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DoesIncludeExist 方法"
ms.assetid: 39751a3d-dfe5-423c-bd94-a53771c3e360
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# DoesIncludeExist
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示文件中是否存在指定头文件的 `#include` 语句。  
  
## 语法  
  
```  
  
      function DoesIncludeExist(   
   oProj,   
   strHeaderFile,   
   strInsertIntoFile    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
 *strHeaderFile*  
 要查找的头文件的名称。  
  
 `strInsertIntoFile`  
 包含头文件（不包括路径）的 `#include` 语句的源文件。  
  
## 返回值  
 如果包含指定的头文件，则为 **true**；否则为 **false**。  
  
## 备注  
 指示 `strInsertIntoFile` 指定的文件中是否存在特定头文件的 \#include 语句。  
  
## 示例  
  
```  
// Check to see if #include for atlbase.h   
// is included in the project's stdafx.h.  
// and add it if it is not.  
if (!DoesIncludeExist(selProj, "<atlbase.h>", strSTDAFX))  
   oCM.AddInclude("<atlbase.h>", strSTDAFX, vsCMAddPositionEnd);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)