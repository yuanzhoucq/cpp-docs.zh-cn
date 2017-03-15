---
title: "SetCommonPchSettings | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SetCommonPchSettings"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SetCommonPchSettings 方法"
ms.assetid: 12f5524b-f654-4222-b979-8ee0d9f58c14
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# SetCommonPchSettings
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

为项目建立预编译头设置。  
  
## 语法  
  
```  
  
      function SetCommonPchSettings(   
   oProj    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
## 备注  
 调用该函数为项目建立预编译头设置。  
  
 此函数将 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A> 属性设置为以下值：  
  
-   **pchUseUsingSpecific** 使用 [\/Yu（使用预编译头文件）](../build/reference/yu-use-precompiled-header-file.md)编译器设置。  
  
-   **pchCreateUsingSpecific** 使用 [\/Yc（创建预编译头文件）](../build/reference/yc-create-precompiled-header-file.md)编译器设置。  
  
## 示例  
  
```  
if ((strAppType == "LIB" || ((strAppType == "CONSOLE") &&   
   wizard.FindSymbol(SUPPORT_MFC"))) && !Pch)  
   {  
      AddFilesToProject(selProj, strProjectName, InfFile);  
      SetNoCommonPchSettings(selProj);  
   }  
else  
   {  
      AddFilesToProject(selProj, strProjectName, InfFile);  
      SetcommonPchSettings(selProj);  
   }  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)   
 [SetNoPchSettings](../ide/setnopchsettings.md)   
 [AddCommonConfig](../ide/addcommonconfig.md)