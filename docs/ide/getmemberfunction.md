---
title: "GetMemberfunction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetMemberFunction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMemberfunction 方法"
ms.assetid: 1e610977-9bc7-4ff2-a79f-132c8e913b4d
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetMemberfunction
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

调用此函数以根据给定名称获取函数对象。  
  
## 语法  
  
```  
  
      function GetMemberfunction(   
   oClass,   
   strFuncName,   
   oProj    
);  
```  
  
#### 参数  
 *oClass*  
 选定的类对象。  
  
 `strFuncName`  
 要检索的函数名。  
  
 `oProj`  
 选定的项目。  
  
## 返回值  
 `strFuncName` 所指示的函数。  
  
## 备注  
 调用此函数以根据给定名称获取函数对象。  有关更多信息，请参见 Visual C\+\+ 代码模型中的 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeModel.Functions%2A>。  
  
## 示例  
  
```  
// Gets the function ExitInstance from the class CWinApp in the   
// current project.  
var oExitInstance = GetMemberFunction(oCWinApp, "ExitInstance", oProj);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)