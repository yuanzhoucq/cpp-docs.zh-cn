---
title: "CreateSafeName | Microsoft Docs"
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
  - "CreateSafeName"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CreateSafeName 方法"
ms.assetid: 3a0dd4af-776d-4c25-aff9-4c539f173cb8
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CreateSafeName
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

生成 C\+\+ 友好名称。  
  
## 语法  
  
```  
  
      function CreateSafeName(   
   strName    
);  
```  
  
#### 参数  
 `strName`  
 旧名称。  
  
## 返回值  
 新的、安全的名称。  
  
## 备注  
 调用该函数以从包含 C\+\+ 无法使用的字符的名称创建 C\+\+ 友好名称。  可接受的 C\+\+ 名称可以包含大写或小写字母、数字或下划线（“\_”）。  
  
 该函数逐字符检查旧名称字符，并跳过任何无法使用的字符。  如果旧名称不包含友好字符，则函数返回“My”作为新名称。  如果新友好名称以数字开头，则该函数用“My”预置新名称。  
  
## 示例  
  
```  
// Get the project name  
var strProjectName = wizard.FindSymbol("PROJECT_NAME");  
  
// Set the project name to the safe project name.   
var strSafeProjectName = CreateSafeName(strProjectName);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)