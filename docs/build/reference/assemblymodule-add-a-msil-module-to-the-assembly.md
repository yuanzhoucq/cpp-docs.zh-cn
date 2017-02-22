---
title: "/ASSEMBLYMODULE（向程序集添加 MSIL 模块） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/assemblymodule"
  - "VC.Project.VCLinkerTool.AddModuleNamesToAssembly"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYMODULE 链接器选项"
  - "程序集 [C++]"
  - "程序集 [C++], 添加模块到"
  - "ASSEMBLYMODULE 链接器选项"
  - "-ASSEMBLYMODULE 链接器选项"
ms.assetid: 67357da8-e4b6-49fd-932c-329a5777f143
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /ASSEMBLYMODULE（向程序集添加 MSIL 模块）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYMODULE:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 要包括在此程序集中的模块。  
  
## 备注  
 \/ASSEMBLYMODULE 选项允许您将模块引用添加到程序集中。  模块中的类型信息将不可用于已添加模块引用的程序集程序。  但是，模块中的类型信息将可用于引用该程序集的所有程序。  
  
 使用 [\#using](../../preprocessor/hash-using-directive-cpp.md) 向程序集添加模块引用，并使模块的类型信息可用于程序集程序。  
  
 例如，考虑以下方案：  
  
1.  用 [\/LN](../../build/reference/ln-create-msil-module.md) 创建模块。  
  
2.  在不同的项目中使用 \/ASSEMBLYMODULE 以将该模块包含在将创建程序集的当前编译中。  该项目将不用 `#using` 引用模块。  
  
3.  引用此程序集的任何项目现在也可以使用该模块中的类型。  
  
 其他影响程序集生成的链接器选项为：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 Visual C\+\+ 链接器接受 .netmodule 文件，因为输入和链接器生成的输出文件是程序集还是 .netmodule 不在输入到链接器的运行时关联任何 .netmodules。有关详细信息，请参阅[用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“输入”属性页。  
  
4.  修改“将模块添加到程序集”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AddModuleNamesToAssembly%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)