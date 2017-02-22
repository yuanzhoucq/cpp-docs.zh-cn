---
title: "GetInterfaceType | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetInterfaceType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetInterfaceType 方法"
ms.assetid: cc6403a8-0c2b-47f7-a8f7-9db95df87d5a
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetInterfaceType
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

获取接口类型。  
  
## 语法  
  
```  
  
      function GetInterfaceType(   
   oInterface    
);  
```  
  
#### 参数  
 *oInterface*  
 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeInterface> 对象。  
  
## 返回值  
 指示接口类型（如 custom、dual、dispinterface 或 oleautomation）的字符串。  
  
## 备注  
 调用该函数以获取接口类型。  
  
## 示例  
 请参见 [GetMaxID](../ide/getmaxid.md)。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetInterfaceClasses](../ide/getinterfaceclasses.md)