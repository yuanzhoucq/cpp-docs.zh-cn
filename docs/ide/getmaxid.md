---
title: "GetMaxID | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetMaxID"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetMaxID 方法"
ms.assetid: a155ec2e-6132-4e40-9b85-d710538778a1
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# GetMaxID
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

从该接口及其所有基的成员获取最高的 dispid。  
  
## 语法  
  
```  
  
      function GetMaxID(   
   ointerface    
);  
```  
  
#### 参数  
 *ointerface*  
 一个 <xref:Microsoft.VisualStudio.VCCodeModel.VCCodeInterface> 对象。  
  
## 返回值  
 来自 *oInterface* 及其所有基的成员的最高 dispid。  
  
## 备注  
 调用该函数以从指定接口及其所有基的成员获取最高的 dispid。  
  
## 示例  
  
```  
if (strInterfaceType == "custom")  
      window.external.AddSymbol("DISPID_DISABLED", true);  
   else  
   {  
      var nDispID = window.external.FindSymbol("DISPID");  
      if (!nDispID.length)  
      {  
         nDispID = GetMaxID(oInterface) + 1;  
         window.external.AddSymbol("DISPID", nDispID);  
      }  
   }  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)