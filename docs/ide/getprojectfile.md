---
title: "GetProjectFile | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "GetProjectFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "GetProjectFile 方法"
ms.assetid: e5fdc468-755a-4b4e-81bd-e63881531bed
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# GetProjectFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

返回指定类型的文件名。  
  
## 语法  
  
```  
  
      function GetProjectFile(   
   oProj,   
   strType,   
   bFullPath,   
   bMFC    
);  
```  
  
#### 参数  
 oProj  
 选定的项目。  
  
 `strType`  
 要检索的文件类型，如 STDAFX、RC、IDL、CPP、H、ODL 或 DEF。  
  
 *bFullPath*  
 指示是否返回完整路径名的标志。  
  
 *bMFC*  
 指示项目是否是基于 MFC 的项目。  如果 `strType` 是 .cpp 或 .h，则认为基于 MFC。  如果不是，则假定项目基于 ATL。  
  
## 返回值  
 每种项目类型文件的文件名。  
  
## 备注  
 调用此函数以获取指定项目中指定类型的文件名。  
  
## 示例  
  
```  
// The selected MFC project's CPP file is retrieved and   
// assigned to strFileName.  
var strFileName = GetProjectFile(selProj, "CPP", false, true);  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [GetProjectPath](../ide/getprojectpath.md)   
 [GetUniqueFileName](../ide/getuniquefilename.md)