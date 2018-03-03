---
title: "HLSL 属性页： 常规 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.FXCompilerTool.ShaderModel
- VC.Project.FXCompilerTool.PreprocessorDefinitions
- VC.Project.FXCompilerTool.ShaderType
- VC.Project.FXCompilerTool.EnableDebuggingInformation
- VC.Project.FXCompilerTool.AdditionalIncludeDirectories
- VC.Project.FXCompilerTool.DisableOptimizations
- VC.Project.FXCompilerTool.EntryPointName
dev_langs:
- C++
ms.assetid: 0e02f2a6-f123-43da-b04b-a0719a7c2b03
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: be548966f6e75afde2c137c8beab38903844667c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/21/2017
---
# <a name="hlsl-property-pages-general"></a>HLSL 属性页：常规
若要配置 HLSL 编译器 (fxc.exe) 的以下属性，使用其**常规**属性页。 有关如何访问**常规**HLSL 文件夹中的属性页上看到[使用项目属性](../ide/working-with-project-properties.md)。  
  
## <a name="uielement-list"></a>UIElement 列表  
 **附加包含目录**  
 将一个或多个目录添加到 include 路径。 使用分号来分隔目录。  
  
 此属性对应于**/I [路径]**命令行自变量。  
  
 **入口点名称**  
 指定的着色器的入口点。 默认情况下，值是**主要**。  
  
 此属性对应于**/E [名称]**命令行自变量。  
  
 **禁用优化**  
 **是 （/ 优化）**禁用优化; 否则为**否**。 默认情况下，值是**是 （/ 优化）**为**调试**配置和**否**为**版本**配置。  
  
 **/Od** HLSL 编译器命令行自变量隐式应用**/Gfp**命令行参数，但输出可能不能与通过传递同时生成的输出相同**/Od**和**/Gfp**命令行自变量显式。  
  
 **启用调试信息**  
 **是 (/Zi)**若要启用调试信息; 否则为**否**。 默认情况下，值是**是 (/Zi)**为**调试**配置和**否**为**版本**配置。  
  
 **着色器类型**  
 指定的着色器的类型。 不同种类的着色器实现图形管道的不同的部分。 某些种类的着色器是仅在较新的着色器模型中可用 (这由**着色器模型**属性) — 例如，计算着色器模型 5 中引入了着色器。  
  
 此属性对应于**[type]**部分**/T [type] _ [型号]** HLSL 编译器命令行自变量。 **着色器模型**属性指定**[型号]**自变量的部分。  
  
 **着色器模型**  
 指定的着色器模型。 不同的着色器模型具有不同的功能。 一般情况下，较新的着色器模型提供扩展的功能，但需要更现代图形硬件以运行着色器代码。 某些种类的着色器 (这由**着色器类型**属性) 只能在较新的着色器模型中使用-例如，计算着色器模型 5 中引入了着色器。  
  
 此属性对应于**[型号]**部分**/T [type] _ [型号]** HLSL 编译器命令行自变量。 **着色器类型**属性指定**[type]**自变量的部分。  
  
 **预处理器定义**  
 将添加一个或多个预处理器符号定义要应用于 HLSL 源代码文件。 使用分号分隔的符号定义。  
  
 此属性对应于**/D [定义]** HLSL 编译器命令行自变量。  
  
## <a name="see-also"></a>请参阅  
 [HLSL 属性页](../ide/hlsl-property-pages.md)   
 [HLSL 属性页： 高级](../ide/hlsl-property-pages-advanced.md)   
 [HLSL 属性页：输出文件](../ide/hlsl-property-pages-output-files.md)