---
title: "/DELAYSIGN（为程序集进行部分签名） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/delaysign"
  - "VC.Project.VCLinkerTool.DelaySign"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYSIGN 链接器选项"
  - "DELAYSIGN 链接器选项"
  - "-DELAYSIGN 链接器选项"
ms.assetid: 15244d30-3ecb-492f-a408-ffe81f38de20
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# /DELAYSIGN（为程序集进行部分签名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DELAYSIGN[:NO]  
```  
  
## 备注  
 其中，  
  
 NO  
 指定程序集不应被部分签名。  
  
## 备注  
 如果只想将公钥放入程序集中，则应使用 **\/DELAYSIGN**。  默认值为 **\/DELAYSIGN:NO**。  
  
 如果不与 [\/KEYFILE](../../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) 或 [\/KEYCONTAINER](../../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md) 一起使用，则 **\/DELAYSIGN** 选项没有任何作用。  
  
 如果要求完全签名的程序集，编译器将对包含清单（程序集元数据）的文件进行散列处理，并用私钥对该散列数据进行签名。  产生的数字签名存储在包含清单的文件中。  如果程序集的签名延迟，则链接器将不会计算和存储签名，但会在文件中保留空间以便以后添加签名。  
  
 例如，使用 **\/DELAYSIGN** 将允许测试人员把程序集放入全局缓存中。  测试完成后，可以通过将私钥放入程序集中对程序集进行完全签名。  
  
 有关对程序集签名的更多信息，请参见 [强名称程序集（程序集签名）](../../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md) 和 [延迟为程序集签名](../Topic/Delay%20Signing%20an%20Assembly.md)。  
  
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