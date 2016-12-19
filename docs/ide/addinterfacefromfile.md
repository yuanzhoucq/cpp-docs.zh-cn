---
title: "AddInterfaceFromFile | Microsoft Docs"
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
  - "AddInterfaceFromFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddInterfaceFromFile 方法"
ms.assetid: fa848690-ad98-4fb4-bbcf-dffcaad05df2
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# AddInterfaceFromFile
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

呈现并插入包含接口的模板文件。  
  
## 语法  
  
```  
  
      function AddInterfaceFromFile(   
   oCM,   
   strInterfaceFile    
);  
```  
  
#### 参数  
 `oCM`  
 [Visual C\+\+ Code Model](http://msdn.microsoft.com/zh-cn/dd6452c2-1054-44a1-b0eb-639a94a1216b) 对象。  
  
 *strInterfaceFile*  
 只是模板文件名（不包括路径）。  
  
## 备注  
 调用该函数以将包含接口的模板文件呈现并插入到项目的 .idl 文件中。  
  
 如果未成功添加接口，则该函数将显示错误信息。  
  
## 示例  
  
```  
// Render myint.idl and insert into strProject.idl  
AddInterfaceFromFile(oCM, "myint.idl");  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)