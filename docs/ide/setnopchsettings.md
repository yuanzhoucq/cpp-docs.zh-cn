---
title: "SetNoPchSettings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetNoPchSettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetNoPchSettings 方法"
ms.assetid: 52373c98-ad5e-4e9b-9e0f-9f58ddb2a636
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# SetNoPchSettings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

当未使用预编译头时，设置项目配置属性。  
  
## 语法  
  
```  
  
      function SetNoPchSettings(   
   oProj    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
## 备注  
 当项目未使用预编译头设置时，调用该函数配置项目。  
  
## 示例  
 请参见 [SetCommonPchSettings](../ide/setcommonpchsettings.md)。  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [SetCommonPchSettings](../ide/setcommonpchsettings.md)   
 [AddCommonConfig](../ide/addcommonconfig.md)