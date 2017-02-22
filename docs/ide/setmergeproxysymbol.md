---
title: "SetMergeProxySymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetMergeProxySymbol"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetMergeProxySymbol 方法"
ms.assetid: d6a9db59-2d5b-4431-98bc-785675e0eafe
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SetMergeProxySymbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此函数由向导调用以在需要时添加 \_MERGE\_PROXYSTUB 符号。  
  
## 语法  
  
```  
  
      function SetMergeProxySymbol(   
   oProj    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目对象。  
  
## 备注  
 此函数由向导调用以在需要时添加 \_MERGE\_PROXYSTUB 符号。  
  
## 示例  
  
```  
SetMergeProxySymbol (selproj);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)