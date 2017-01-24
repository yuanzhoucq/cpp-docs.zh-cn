---
title: "CanAddMFCClass | Microsoft Docs"
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
  - "CanAddMFCClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddMFCClass 方法"
ms.assetid: 6a97a410-b028-4aad-9b06-04c12cf481eb
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CanAddMFCClass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由向导调用以验证用户是否可向项目中添加 MFC 类。  
  
## 语法  
  
```  
  
      function CanAddMFCClass(   
   oProj,   
   oObject    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目  
  
 `oObject`  
 选定的对象。  在此情况下为当前项目。  
  
## 返回值  
 如果可以添加类，则为 **true**；如果用户对某个项目调用此函数，而该项目不是 MFC 项目并且不具有 MFC 支持，则为 **false**。  
  
## 备注  
 由向导调用以验证该项目是否与即将运行的代码向导兼容（换句话说，它是否可以接受 MFC 类）。  
  
 当参数 PREPROCESS\_FUNCTION 在[项目控件的 .vsz 文件](../ide/dot-vsz-file-project-control.md)中时，向导调用此函数。它检查 [Visual C\+\+ 代码模型](http://msdn.microsoft.com/zh-cn/dd6452c2-1054-44a1-b0eb-639a94a1216b)对象是否可用。  如果代码模型不可用，该函数将报告错误并且返回 **false**。  
  
## 示例  
  
```  
// Determine if an MFC class can be added to the project  
if (CanAddMFCClass(selProj, selObj))  
{  
   return true;  
}  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [CanAddClass](../ide/canaddclass.md)   
 [CanAddATLClass](../ide/canaddatlclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)