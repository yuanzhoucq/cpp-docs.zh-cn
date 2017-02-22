---
title: "InsertIntoFunction | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "InsertIntoFunction"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "InsertIntoFunction 方法"
ms.assetid: 50500c3c-bee3-4a9c-a403-7dcd752de23c
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# InsertIntoFunction
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由 [AddATLSupportToProject](../ide/addatlsupporttoproject.md) 用来将代码插入 [InitInstance](../Topic/CWinApp::InitInstance.md) 中。  
  
## 语法  
  
```  
  
      function InsertIntoFunction(   
   oFunction,   
   strSearchString,   
   nStartLine,   
   nEndLine,   
   bInsideIfBlock    
);  
```  
  
#### 参数  
 *oFunction*  
 对其执行插入的函数对象。  
  
 `strSearchString`  
 为确定插入点而查找的字符串。  
  
 *nStartLine*  
 要传递到 [GetCodeForInitInstance](../ide/getcodeforinitinstance.md) 的起始行。  
  
 *nEndLine*  
 要传递到 [GetCodeForInitInstance](../ide/getcodeforinitinstance.md) 的结束行。  
  
 *bInsideIfBlock*  
 指示是否插入函数块中。  
  
## 返回值  
 如果成功，则为 **true**；否则为 **false**。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetMemberfunction](../ide/getmemberfunction.md)