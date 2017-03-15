---
title: "GetInterfaceClasses | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetInterfaceClasses"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInterfaceClasses 方法"
ms.assetid: 712c112f-b4ff-43c4-ad49-c4f4c13c48bd
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetInterfaceClasses
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回与接口关联的 `VCCodeClass` 对象。  
  
## 语法  
  
```  
  
      function GetInterfaceClasses(   
   strInterface,   
   oProject,   
   aryClasses    
);  
```  
  
#### 参数  
 *strInterface*  
 包含类对象的接口的名称。  
  
 *oProject*  
 选定的项目。  
  
 *aryClasses*  
 \[out\] 接口中的类对象数组。  
  
## 返回值  
 与接口关联的 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeClass> 对象。  
  
## 备注  
 调用该函数以检索与接口关联的类。  
  
## 示例  
  
```  
var aryClasses = new Array();  
GetInterfaceClasses(oInterface.Name, selProj, aryClasses);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetInterfaceType](../ide/getinterfacetype.md)