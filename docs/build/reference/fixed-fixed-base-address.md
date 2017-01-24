---
title: "/FIXED（固定基址） | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/fixed"
  - "VC.Project.VCLinkerTool.FixedBaseAddress"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/FIXED 链接器选项"
  - "FIXED 链接器选项"
  - "-FIXED 链接器选项"
  - "用于加载程序的首选基址"
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /FIXED（固定基址）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/FIXED[:NO]  
```  
  
## 备注  
 通知操作系统只在其首选基址加载程序。  如果首选基址不可用，则操作系统将不加载该文件。  有关详细信息，请参阅[\/BASE（基址）](../../build/reference/base-base-address.md)。  
  
 \/FIXED:NO 是DLL 的默认设置，\/FIXED 是任何其他项目类型的默认设置。  
  
 当指定 \/FIXED 时，LINK 不生成程序中的重定位节。  在运行时，如果操作系统无法在指定的地址加载程序，它将发出错误信息并且不加载该程序。  
  
 指定 \/FIXED:NO 以在程序中生成重定位节。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[使用项目属性](../../ide/working-with-project-properties.md)。  
  
2.  选择 **Linker** 文件夹。  
  
3.  选择**“命令行”**属性页。  
  
4.  键入选项名并在 **“其他选项”** 框中设置。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)