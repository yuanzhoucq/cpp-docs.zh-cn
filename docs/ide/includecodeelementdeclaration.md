---
title: "IncludeCodeElementDeclaration | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IncludeCodeElementDeclaration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IncludeCodeElementDeclaration 方法"
ms.assetid: 714e76e4-76bc-439a-982a-cf9d4ada7677
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# IncludeCodeElementDeclaration
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将 include 语句添加到 `strInFile`，包括实现 `strCodeElemName` 的头（如果在 `oProj` 中找到这样的头）。  
  
## 语法  
  
```  
  
      function IncludeCodeElementDeclaration(   
   oProj,   
   strCodeElemName,   
   strInFile    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
 `strCodeElemName`  
 正在搜索其定义头的代码元素的全名。  
  
 `strInFile`  
 将包含定义头（如果找到）的文件。  
  
## 备注  
 将 include 语句添加到 `strInFile`，包括实现 `strCodeElemName` 的头（如果在 `oProj` 中找到这样的头）。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)