---
title: "/LARGEADDRESSAWARE（处理大地址） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.LargeAddressAware"
  - "/largeaddressaware"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LARGEADDRESSAWARE 链接器选项"
  - "LARGEADDRESSAWARE 链接器选项"
  - "-LARGEADDRESSAWARE 链接器选项"
ms.assetid: a29756c8-e893-47a9-9750-1f0d25359385
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /LARGEADDRESSAWARE（处理大地址）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LARGEADDRESSAWARE[:NO]  
```  
  
## 备注  
 \/LARGEADDRESSAWARE 选项通知链接器应用程序可以处理大于 2 GB 的地址。  在 64 位编译器中，默认情况下启用此选项。  在 32 位编译器中，如果未在链接器行上指定 \/LARGEADDRESSAWARE，则将启用 \/LARGEADDRESSAWARE:NO。  
  
 如果用 \/LARGEADDRESSAWARE 来链接应用程序，则 DUMPBIN [\/HEADERS](../../build/reference/headers.md) 将显示该效果的信息。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“系统”属性页。  
  
4.  修改“启用大地址”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LargeAddressAware%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)