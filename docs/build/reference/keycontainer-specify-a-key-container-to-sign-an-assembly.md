---
title: "/KEYCONTAINER（指定密钥容器以便为程序集签名） | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.KeyContainer"
  - "/keycontainer"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/KEYCONTAINER 链接器选项"
  - "KEYCONTAINER 链接器选项"
  - "-KEYCONTAINER 链接器选项"
ms.assetid: 94882d12-b77a-49c7-96d0-18a31aee001e
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /KEYCONTAINER（指定密钥容器以便为程序集签名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/KEYCONTAINER:name  
```  
  
## 备注  
 其中，  
  
 *name*  
 包含密钥的容器。  如果字符串包含空格，则将其放置在双引号 \(" "\) 中。  
  
## 备注  
 链接器通过将公钥插入程序集清单并用私钥对最终的程序集签名来创建签名的程序集。  若要生成密钥文件，请在命令行上键入 [sn \-k](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) `file`。  **sn \-i** 将密钥对安装到容器中。  
  
 如果用 [\/LN](../../build/reference/ln-create-msil-module.md) 进行编译，则将密钥文件的名称保存在模块中。如果程序集包含对该模块的显式引用（通过 [\#using](../../preprocessor/hash-using-directive-cpp.md)），在对这些程序集进行编译时或使用 [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) 进行链接时，就会将密钥文件的名称合并到创建的程序集中。  
  
 也可以通过 [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 将加密信息传递给编译器。  如果需要部分签名的程序集，则应使用 [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)。  有关对程序集签名的更多信息，请参见 [强名称程序集（程序集签名）](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 其他影响程序集生成的链接器选项为：  
  
-   [\/ASSEMBLYDEBUG](../../build/reference/assemblydebug-add-debuggableattribute.md)  
  
-   [\/ASSEMBLYLINKRESOURCE](../../build/reference/assemblylinkresource-link-to-dotnet-framework-resource.md)  
  
-   [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md)  
  
-   [\/ASSEMBLYRESOURCE](../../build/reference/assemblyresource-embed-a-managed-resource.md)  
  
-   [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)