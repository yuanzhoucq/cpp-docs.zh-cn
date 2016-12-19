---
title: "GetExportPragmas | Microsoft Docs"
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
  - "GetExportPragmas"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetExportPragmas 方法"
ms.assetid: ef21f6a3-d83f-4e19-9323-ca28cc40c8fd
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# GetExportPragmas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

添加导出函数的杂注。  
  
## 语法  
  
```  
  
function GetExportPragmas( );  
  
```  
  
## 返回值  
 包含导出杂注的字符串。  可以是如下内容之一：  
  
-   `#pragma comment(linker, "/EXPORT:DllCanUnloadNow=_DllCanUnloadNow@0,PRIVATE")'`  
  
-   `#pragma comment(linker, "/EXPORT:DllGetClassObject=_DllGetClassObject@12,PRIVATE")`  
  
-   `#pragma comment(linker, "/EXPORT:DllRegisterServer=_DllRegisterServer@0,PRIVATE")`  
  
-   `#pragma comment(linker, "/EXPORT:DllUnregisterServer=_DllUnregisterServer@0,PRIVATE")`  
  
## 备注  
 调用该函数以添加导出函数的杂注。  
  
## 示例  
  
```  
oDllCanUnloadNow.StartPoint.Insert(GetExportPragmas() + "\r\n");  
oCM.Synchronize();  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [注释](../preprocessor/comment-c-cpp.md)