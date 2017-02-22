---
title: "/MANIFESTDEPENDENCY（指定清单依赖项） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.AdditionalManifestDependencies"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/MANIFESTDEPENDENCY 链接器选项"
  - "MANIFESTDEPENDENCY 链接器选项"
  - "-MANIFESTDEPENDENCY 链接器选项"
ms.assetid: e4b68313-33a2-4c3e-908e-ac2b9f7d6a73
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# /MANIFESTDEPENDENCY（指定清单依赖项）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/MANIFESTDEPENDENCY:manifest_dependency  
```  
  
## 备注  
 \/MANIFESTDEPENDENCY 使您可以指定将要置于清单文件 \<dependency\>节中的特性。  
  
 有关如何创建清单文件的信息，请参见 [\/MANIFEST（创建并行程序集清单）](../../build/reference/manifest-create-side-by-side-assembly-manifest.md)。  
  
 有关清单文件的 \<dependency\> 部分的更多信息，请参见[Publisher Configuration Files](http://msdn.microsoft.com/library/aa375682).  
  
 \/MANIFESTDEPENDENCY 信息可通过以下两种方式之一传递给链接器：  
  
-   直接在命令行（或响应文件）中使用 \/MANIFESTDEPENDENCY 传递。  
  
-   通过 [comment](../../preprocessor/comment-c-cpp.md) 杂注传递。  
  
 下面的示例演示如何通过杂注传递 \/MANIFESTDEPENDENCY 注释。  
  
```  
#pragma comment(linker, "\"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"")  
```  
  
 此示例可在清单文件中产生下列项：  
  
```  
<dependency>  
  <dependentAssembly>  
    <assemblyIdentity type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*' />  
  </dependentAssembly>  
</dependency>  
```  
  
 相同的 \/MANIFESTDEPENDENCY 注释还可在命令行中按以下方式传递：  
  
```  
"/manifestdependency:type='Win32' name='Test.Research.SampleAssembly' version='6.0.0.0' processorArchitecture='X86' publicKeyToken='0000000000000000' language='*'\"  
```  
  
 链接器将收集 \/MANIFESTDEPENDENCY 注释，消除重复项，然后将得到的 XML 字符串添加到清单文件中。如果链接器发现冲突项，清单文件将会损坏，而应用程序的启动也将失败（可能会在事件日志中添加一项，指示故障来源）。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“清单文件”**属性页。  
  
5.  修改**“附加清单依赖项”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalManifestDependencies%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)