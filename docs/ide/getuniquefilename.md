---
title: "GetUniqueFileName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetUniqueFileName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetUniqueFilename 方法"
ms.assetid: f9760e1a-82d0-4d8b-b00a-6f4c36f6b2c6
caps.latest.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 8
---
# GetUniqueFileName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回唯一的文件名。  
  
## 语法  
  
```  
  
      function GetUniqueFileName(   
   strDirectory,   
   strFileName    
);  
```  
  
#### 参数  
 *strDirectory*  
 在其中查找文件名的目录。  
  
 `strFileName`  
 要检查的文件名。  
  
## 返回值  
 如果唯一，则为 `strFileName` 中指示的文件名；否则该函数返回 `strFileName`（追加一个从 1 到 9999999 之间的数字）以使其唯一。  如果未提供 `strFileName`，则该函数通过使用 [GetTempName 方法](jsmthGetTempName)返回唯一的文件名。  
  
## 备注  
 返回唯一的文件名。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetProjectFile](../ide/getprojectfile.md)