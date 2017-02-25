---
title: "AddATLSupportToProject | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddATLSupportToProject 方法"
ms.assetid: 26708f22-1e9b-4432-83b2-ed94c765b753
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# AddATLSupportToProject
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

向 MFC 项目添加 ATL 支持。  
  
## 语法  
  
```  
  
      function AddATLSupportToProject(   
   oProj   
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
## 返回值  
 如果 ATL 支持已成功添加到 MFC 项目，则返回值为 **true**。  
  
## 备注  
 使用该函数将 ATL 支持添加到向导创建的 MFC 项目。  
  
 向导显示一个消息框，确认是否向 MFC 项目添加 ATL 支持。  确认后，向导检查现有支持，并添加全部所需 GUID、模板、头和附加功能，以便向导所创建的 MFC 项目支持 ATL。  
  
## 示例  
  
```  
var oCM = selProj.CodeModel;  
var L_TRANSACTION_Text = "Add ATL Support To Project";  
oCM.StartTransaction(L_TRANSACTION_Text);  
var bRet = AddATLSupportToProject(selProj);  
if (bRet)  
   oCM.CommitTransaction();  
else  
   oCM.AbortTransaction();  
return bRet;  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [CanAddATLClass](../ide/canaddatlclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)   
 [ATL 介绍](../atl/introduction-to-atl.md)