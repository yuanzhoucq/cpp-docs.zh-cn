---
title: "SetErrorInfo | Microsoft Docs"
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
  - "SetErrorInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetErrorInfo 方法"
ms.assetid: 78bca763-3f90-4e04-b566-b4b7fe2431b1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# SetErrorInfo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由 [OnWizFinish](../ide/onwizfinish.md) 和 [CanUseFileName](../ide/canusefilename.md) 调用以提供当前的错误信息。  
  
## 语法  
  
```  
  
      function SetErrorInfo(   
   oErrorObj   
);  
```  
  
#### 参数  
 *oErrorObj*  
 错误对象。  
  
## 备注  
 由 [OnWizFinish](../ide/onwizfinish.md) 和 [CanUseFileName](../ide/canusefilename.md) 调用以提供当前的错误信息。  有关更多信息，请参见 Visual C\+\+ 向导模型文档中的 <xref:Microsoft.VisualStudio.VsWizard.VCWizCtlClass.SetErrorInfo%2A>。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)