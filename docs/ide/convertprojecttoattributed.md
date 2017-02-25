---
title: "ConvertProjectToAttributed | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConvertProjectToAttributed"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ConvertProjectToAttributed 方法"
ms.assetid: 56a2d6e1-7e8e-4595-b2be-ade026593798
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# ConvertProjectToAttributed
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

将 ATL 非特性化项目转换为特性化。  
  
## 语法  
  
```  
  
function ConvertProjectToAttributed( );  
  
```  
  
## 返回值  
 如果已成功转换项目，则为 **true**；否则为 **false**。  
  
## 备注  
 调用该函数将 ATL 项目从非特性化转换为特性化。  有关更多信息，请参见[特性化编程](../windows/attributed-programming-concepts.md)。  
  
## 示例  
  
```  
// Create a function called CheckAddtoProject.  
function CheckAddtoProject(oProj)  
{  
// Is the project attributed already?  
   try  
   {  
      if (!IsAttributedProject(wizard))  
      {  
         // If the project is not converted to attributed, return false.  
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
 [CanAddNonAttributed](../ide/canaddnonattributed.md)