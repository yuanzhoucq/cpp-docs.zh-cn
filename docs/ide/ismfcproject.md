---
title: "IsMFCProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IsMFCProject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IsMFCProject 方法"
ms.assetid: 98dd57df-9fdb-40d7-afcf-4b99e9d54dad
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# IsMFCProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

检查项目是否基于 MFC。  
  
## 语法  
  
```  
  
      function IsMFCProject(   
   oProj,   
   bCWinAppRequired    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目  
  
 *bCWinAppRequired*  
 指示检查中是否包含扩展 DLL。  
  
## 返回值  
 如果项目是 MFC 项目，则为 **true**；否则为 **false**。  
  
## 备注  
 使用此函数确定选定项目是否是 MFC 项目。  
  
## 示例  
  
```  
if (!IsMFCProject(selProj, true))  
   {  
      if (gbExceptionThrown)  
         return false;  
      var L_ErrMsg2_Text = "ATL support can only be added to MFC EXEs or MFC Regular DLLs.";  
      wizard.ReportError(L_ErrMsg2_Text);  
      return false;  
   }  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [IsATLProject](../ide/isatlproject.md)   
 [IsAttributedProject](../ide/isattributedproject.md)