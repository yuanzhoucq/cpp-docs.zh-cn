---
title: "/ASSEMBLYDEBUG（添加 DebuggableAttribute） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.AssemblyDebug"
  - "/ASSEMBLYDEBUG"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ASSEMBLYDEBUG 链接器选项"
  - "ASSEMBLYDEBUG 链接器选项"
  - "-ASSEMBLYDEBUG 链接器选项"
ms.assetid: 94443af3-470c-41d7-83a0-7434563d7982
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /ASSEMBLYDEBUG（添加 DebuggableAttribute）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ASSEMBLYDEBUG[:DISABLE]  
```  
  
 \/ASSEMBLYDEBUG 发出 **DebuggableAttribute** 特性并启用调试信息跟踪，但禁用 JIT 优化。  这等同于在源中指定以下特性：  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
 \/ASSEMBLYDEBUG:DISABLE 发出 **DebuggableAttribute** 特性并禁用调试信息跟踪，但启用 JIT 优化。  这等同于在源中指定以下特性：  
  
```  
[assembly:Debuggable(false, false)];   // same as /ASSEMBLYDEBUG:DISABLE  
```  
  
 默认设置为不发出 **DebuggableAttribute** 特性。  
  
 还可以直接在源代码中将 DebuggableAttribute 添加到程序集。  例如，  
  
```  
[assembly:Debuggable(true, true)];   // same as /ASSEMBLYDEBUG  
```  
  
## 备注  
 在 Visual C\+\+ .NET 2003 及更高版本中，有必要显式指定托管映像是可调试的。  仅使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 是不够的。  
  
 其他影响程序集生成的链接器选项为：  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
-   [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“调试”属性页。  
  
4.  修改“可调试程序集”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AssemblyDebug%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)