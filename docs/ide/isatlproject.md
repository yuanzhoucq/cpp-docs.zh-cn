---
title: "IsATLProject | Microsoft Docs"
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
  - "IsATLProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsATLProject 方法"
ms.assetid: 811115af-5bcd-4ce2-a514-34de4c7419ea
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# IsATLProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示项目是否基于 ATL。  
  
## 语法  
  
```  
  
      function IsATLProject(   
   oProj    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
## 返回值  
 如果项目是 ATL 项目，则为 **true**；否则为 **false**。  
  
## 备注  
 指示项目是否基于 ATL。  
  
## 示例  
  
```  
function CanAddATLSupport(selProj, selObj)  
{  
   if (IsATLProject(selProj))  
   {  
      var L_ErrMsg1_Text = "Current project already has ATL support.";  
      wizard.ReportError(L_ErrMsg1_Text);  
      return false;  
   }  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [IsAttributedProject](../ide/isattributedproject.md)