---
title: "IsAttributedProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IsAttributedProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsAttributedProject 方法"
ms.assetid: 8fe41c0c-40e7-42be-8e15-94a2bbbe87cc
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# IsAttributedProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

指示项目是否已特性化。  
  
## 语法  
  
```  
  
      function IsAttributedProject(   
   owizard    
);  
```  
  
#### 参数  
 *owizard*  
 向导对象。  
  
## 返回值  
 如果项目已特性化，则为 **true**；否则为 **false**。  
  
## 备注  
 指示项目是否已特性化。  
  
## 示例  
  
```  
function CheckAddtoProject(oProj)  
{  
   try  
   {  
      if (!IsAttributedProject(wizard))  
      {  
         if (!ConvertProjectToAttributed(oProj))  
            return false;  
       }  
   }  
   catch (e)  
   {  
      var L_ErrMsg1_Text = "Error in CheckAddtoProject: ";  
         wizard.ReportError( L_ErrMsg1_Text + e.description);  
         return false;  
   }  
  
   return true;  
}  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [IsATLProject](../ide/isatlproject.md)   
 [IsMFCProject](../ide/ismfcproject.md)