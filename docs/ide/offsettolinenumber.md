---
title: "OffsetToLineNumber | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "OffsetToLineNumber"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OffsetToLineNumber 函数"
ms.assetid: ac7e3c22-6b3b-432c-85cc-b50bbef9ce8c
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# OffsetToLineNumber
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

由 [InsertIntoFunction](../ide/insertintofunction.md) 调用以将函数体中的索引转换为行号。  
  
## 语法  
  
```  
  
      function OffsetToLineNumber(   
   strString,   
   nPos    
);  
```  
  
#### 参数  
 `strString`  
 包含函数体的字符串。  函数体是多行字符串，其中的行由 cr\-lf 字符对分隔。  
  
 `nPos`  
 在字符串中的位置。  
  
## 返回值  
 函数体中 `nPos` 所在的行。  函数中的第一行被认为是行 1（不是 0）。  
  
## 备注  
 查找函数体中给定位置的行号。  
  
 该函数由 `InsertIntoFunction` 调用以将函数体中位于 `nPos` 处的索引转换为行号。  
  
## 示例  
  
```  
strString = "function DelFile(fso,  
 strWizTempFile)\r\n{\r\n\ttry\r\n\t{\r\nif   
(fso.FileExists(strWizTempFile))\r\nreturn true;\r\n";  
  
nLine =  OffsetToLineNumber(strString, 60);  
  
// The return value for the above is 5, because character 60 in the string   
// occurs in the 5th line within the string.  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [LineBeginsWith](../ide/linebeginswith.md)