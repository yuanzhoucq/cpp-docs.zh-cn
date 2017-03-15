---
title: "CanAddClass | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CanAddClass"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CanAddClass 方法"
ms.assetid: 76739742-1e34-470c-910d-8784f0adfbf0
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# CanAddClass
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由向导调用以验证项目是否与用户尝试运行的代码向导兼容。  
  
## 语法  
  
```  
  
      function CanAddClass(   
   oProj,   
   oObject    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
 `oObject`  
 选定的对象。  在此情况下为当前项目。  
  
## 返回值  
 如果可以添加类，则为 **true**；否则为 **false**。  
  
## 备注  
 当参数 PREPROCESS\_FUNCTION 在[项目控件的 .vsz 文件](../ide/dot-vsz-file-project-control.md)中时，向导调用此函数。  
  
 它验证 [Visual C\+\+ 代码模型](http://msdn.microsoft.com/zh-cn/dd6452c2-1054-44a1-b0eb-639a94a1216b)对象是否可用。  如果代码模型不可用，该函数将报告错误并且返回 **false**。  
  
## 示例  
  
```  
// Determine if a class can be added to the project  
if (CanAddClass(selProj, selObj))  
{  
   return true;  
}  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [CanAddMFCClass](../ide/canaddmfcclass.md)   
 [CanAddATLClass](../ide/canaddatlclass.md)   
 [IsMFCProject](../ide/ismfcproject.md)