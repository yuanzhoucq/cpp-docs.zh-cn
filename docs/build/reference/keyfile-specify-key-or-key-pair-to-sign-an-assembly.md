---
title: "/KEYFILE（指定密钥或密钥对以便为程序集签名） | Microsoft Docs"
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
  - "/keyfile"
  - "VC.Project.VCLinkerTool.KeyFile"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/KEYFILE 链接器选项"
  - "KEYFILE 链接器选项"
  - "-KEYFILE 链接器选项"
ms.assetid: 9b71f8c0-541c-4fe5-a0c7-9364f42ecb06
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /KEYFILE（指定密钥或密钥对以便为程序集签名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/KEYFILE:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 包含密钥的文件。  如果字符串包含空格，则将其放置在双引号 \(" "\) 中。  
  
## 备注  
 链接器将公钥插入程序集清单中，然后用私钥对最终的程序集进行签名。  若要生成密钥文件，请在命令行上键入 [sn \-k](../Topic/Sn.exe%20\(Strong%20Name%20Tool\).md) `file`。  称签名的程序集具有强名称。  
  
 如果用 [\/LN](../../build/reference/ln-create-msil-module.md) 进行编译，则将密钥文件的名称保存在模块中。如果程序集包含对该模块的显式引用（通过 [\#using](../../preprocessor/hash-using-directive-cpp.md)），在对这些程序集进行编译时或使用 [\/ASSEMBLYMODULE](../../build/reference/assemblymodule-add-a-msil-module-to-the-assembly.md) 进行链接时，就会将密钥文件的名称合并到创建的程序集中。  
  
 也可以通过 [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) 将加密信息传递给链接器。  如果需要部分签名的程序集，则应使用 [\/DELAYSIGN](../../build/reference/delaysign-partially-sign-an-assembly.md)。  有关对程序集签名的更多信息，请参见 [强名称程序集（程序集签名）](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)。  
  
 在同时指定 **\/KEYFILE** 和 **\/KEYCONTAINER** 的情况下（通过命令行选项或自定义特性），链接器将首先尝试密钥容器。  如果成功，则使用密钥容器中的信息对程序集进行签名。  如果链接器没有找到密钥容器，它将尝试使用 \/KEYFILE 指定的文件。  如果成功，则使用密钥文件中的信息对程序集进行签名，并且将把密钥信息安装到密钥容器中（类似 sn \-i），这样，下次编译时密钥容器将是有效的。  
  
 请注意，密钥文件可能只包含公钥。  
  
 有关对程序集签名的更多信息，请参见[创建和使用具有强名称的程序集](../Topic/Creating%20and%20Using%20Strong-Named%20Assemblies.md)。  
  
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