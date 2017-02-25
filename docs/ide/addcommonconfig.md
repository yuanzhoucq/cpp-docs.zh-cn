---
title: "AddCommonConfig | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AddCommonConfig"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AddCommonConfig 方法"
ms.assetid: 16abad93-6dd0-4daa-bf76-91eb6ffbdffa
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# AddCommonConfig
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

向项目中添加默认配置。  
  
## 语法  
  
```  
  
      function AddCommonConfig(   
   oProj,   
   strProjectName    
);  
```  
  
#### 参数  
 `oProj`  
 选定的项目。  
  
 `strProjectName`  
 项目的名称。  
  
## 备注  
 调用该函数将默认代码模型配置添加到向导创建的项目中。  可以指定“Release”配置，也可以指定“Debug”配置。  下表列出每种配置类型的代码模型对象的默认属性设置。  
  
### Visual C\+\+ 编译器工具对象  
  
|对象属性|“Release”配置设置|“Debug”配置设置|  
|----------|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>|pchUseUsingSpecific|pchUseUsingSpecific|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WarningLevel%2A>|3|3|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.MinimalRebuild%2A>|不适用|true|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DebugInformationFormat%2A>|debugEnabled|debugEditAndContinue|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>|optimizeMaxSpeed|不适用|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.BasicRuntimeChecks%2A>|不适用|runtimeBasicCheckAll|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>|true|true|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OmitFramePointers%2A>|true|不适用|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableFunctionLevelLinking%2A>|true|不适用|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.StringPooling%2A>|true|不适用|  
  
### Visual C\+\+ Configuration 对象  
  
|对象属性|“Release”配置设置|“Debug”配置设置|  
|----------|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.IntermediateDirectory%2A>|Release|Debug|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.OutputDirectory%2A>|Release|Debug|  
  
### Visual C\+\+ 链接器工具对象  
  
|对象属性|“Release”配置设置|“Debug”配置设置|  
|----------|-------------------|-----------------|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SubSystem%2A>|subSystemWindows|subSystemWindows|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TargetMachine%2A>|machineX86|machineX86|  
|<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>|true|true|  
  
## 示例  
  
```  
// Create the Visual C++ project.  
selProj = CreateProject(strProjectName, strProjectPath);  
// Add the common configuration to the project.  
   AddCommonConfig(selProj, strProjectName);  
   selProj.Object.keyword = "MyProj";  
```  
  
## 请参阅  
 [用公共 JScript 函数自定义 C\+\+ 向导](../ide/customizing-cpp-wizards-with-common-jscript-functions.md)   
 [用于 C\+\+ 向导的 JScript 函数](../ide/jscript-functions-for-cpp-wizards.md)   
 [创建自定义向导](../ide/creating-a-custom-wizard.md)   
 [设计向导](../ide/designing-a-wizard.md)