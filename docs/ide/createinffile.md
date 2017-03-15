---
title: "CreateInfFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CreateInfFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateInfFile 方法"
ms.assetid: 941ea2ce-db10-428e-b423-8dc2a7e825cf
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# CreateInfFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

创建向导的 Templates.inf 文件。  
  
## 语法  
  
```  
  
function CreateInfFile( );  
  
```  
  
## 返回值  
 向导模板文件。  
  
## 备注  
 调用该函数以根据用户的选择从 Templatesinf.txt 创建向导的 Templates.inf 文件。Templatesinf.txt 是该函数首先在临时目录中创建的临时文本文件。  Templates.inf 包含向导创建的文件名列表。  有关更多信息，请参见[模板文件](../ide/template-files.md)。  
  
 如果该函数无法在临时目录中创建 Templatesinf.txt 文件，则显示错误。  
  
## 示例  
 请参见 [AddFilesToProject](../ide/addfilestoproject.md)。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [AddFilesToProject](../ide/addfilestoproject.md)   
 [SetFilters](../ide/setfilters.md)   
 [AddFilesToProject](../ide/addfilestoproject.md)