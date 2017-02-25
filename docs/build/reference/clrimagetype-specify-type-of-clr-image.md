---
title: "/CLRIMAGETYPE（指定 CLR 映像的类型） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/CLRIMAGETYPE"
  - "VC.Project.VCLinkerTool.CLRImageType"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRIMAGETYPE 链接器选项"
  - "-CLRIMAGETYPE 链接器选项"
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
caps.latest.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 14
---
# /CLRIMAGETYPE（指定 CLR 映像的类型）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/CLRIMAGETYPE:{IJW|PURE|SAFE|SAFE32BITPREFERRED}  
```  
  
## 备注  
 链接器接受使用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md)，\/clr，生成的本机对象，MSIL 对象：\/clr:pure 或 \/clr:safe。  在同一个生成中混合对象被传递时，默认情况下结果输出文件的可验证性级别等于输入模块的最低可验证性级别。  例如，如果将 safe 和 pure 模块传递给链接器，则输出文件为 pure。  如果传递本机映像和混合模式映像（使用 **\/clr** 编译），则结果映像为混合模式映像。  
  
 你可以看到\/CLRIMAGETYPE 根据需要指定较低级别的可验证性。  
  
 .NET 4.5 中，\/CLRIMAGETYPE 支持 SAFE32BITPREFERRED 选项。  这将指示图像标志的 PE 标头 MSIL 对象是安全的，并且可以运行在所有平台，但是，32 位执行环境首选方法。  此选项在 ARM 平台使应用程序运行并指定应运行在 64 位操作系统上的 WOW64 下而不是使用 64 位执行环境。  
  
 当在 64 位操作系统上使用 **\/clr** 或 **\/clr:pure** 编译的 .exe 时，应用程序将在 WOW64 下运行，它允许 32 位应用程序在 64 位操作系统上运行。  默认情况下，编译使用 **\/clr:safe** 的 .exe 运行在 64 位操作系统上的下受支持。  但是，安全应用程序可以加载 32 位组件。  在此情况下，在操作系统的 64 位支持下运行的安全映像将在加载 32 位应用程序时失败。  若要确保一个安全的图像继续运行，则在 64 位操作系统时加载 32 位组件，请使用 \/CLRIMAGETYPE:SAFE32BITPREFERRED 选项。  如果您的代码在 ARM 平台不能运行，可以指定 \/CLRIMAGETYPE:PURE 选项更改元数据 \(.corflags\)，指示要运行的方式在 WOW64 下运行 \(和替换您的入口符号\):  
  
 **cl \/clr:safe t.cpp \/link \/clrimagetype:pure \/entry:?main@@$$HYMHXZ \/subsystem:console**  
  
 有关如何确定文件的 CLR 映像类型的信息，请参见 [\/CLRHEADER](../../build/reference/clrheader.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[如何：打开项目属性页](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“高级”**属性页。  
  
5.  修改**“CLR 映像类型”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)