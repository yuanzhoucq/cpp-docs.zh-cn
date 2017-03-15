---
title: "/AI（指定元数据目录） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCCLCompilerTool.AdditionalUsingDirectories"
  - "VC.Project.VCNMakeTool.AssemblySearchPath"
  - "/AI"
  - "VC.Project.VCCLWCECompilerTool.AdditionalUsingDirectories"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/AI 编译器选项 [C++]"
  - "AI 编译器选项 [C++]"
  - "-AI 编译器选项 [C++]"
ms.assetid: fb9c1846-504c-4a3b-bb39-c8696de32f6f
caps.latest.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 13
---
# /AI（指定元数据目录）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定在解析传递给 `#using` 指令的文件引用时编译器将搜索的目录。  
  
## 语法  
  
```  
/AIdirectory  
```  
  
## 参数  
 `directory`  
 编译器要搜索的目录或路径。  
  
## 备注  
 只能将一个目录传递给 **\/AI** 调用。  为要编译器搜索的每个路径指定一个 **\/AI** 选项。  例如，若要将 C:\\Project\\Meta 和 C:\\Common\\Meta 添加到 `#using` 指令的编译器搜索路径，请将 `/AI"C:\Project\Meta" /AI"C:\Common\Meta"` 添加到编译器命令行或将每个目录添加到 Visual Studio 中的**“其他 \#using 目录”**属性。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  在导航窗格中，依次选择**“配置属性”**、**“C\/C\+\+”**和**“常规”**。  
  
3.  修改**“其他 \#using 目录”**属性。  
  
### 以编程方式设置此编译器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalUsingDirectories%2A>。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)   
 [\#using 指令](../../preprocessor/hash-using-directive-cpp.md)