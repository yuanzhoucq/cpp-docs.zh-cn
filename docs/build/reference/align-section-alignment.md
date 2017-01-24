---
title: "/ALIGN（节对齐） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.Alignment"
  - "/align"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALIGN 链接器选项"
  - "ALIGN 链接器选项"
  - "-ALIGN 链接器选项"
  - "节对齐"
  - "节"
  - "节, 指定对齐方式"
ms.assetid: f2f8ac24-e90e-4bea-8205-f2960a3b1740
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALIGN（节对齐）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/ALIGN[:number]  
```  
  
## 备注  
 其中：  
  
 `number`  
 对齐值。  
  
## 备注  
 \/ALIGN 选项指定程序的线性地址空间内的每个部分的对齐方式。  `number` 参数以字节为单位，并且必须是 2 的幂。  默认值是 4K \(4096\)。  如果对齐方式产生无效的图像，则链接器发出警告。  
  
 除非正在编写诸如设备驱动程序的应用程序，否则应不需要修改对齐方式。  
  
 可以用 [\/SECTION](../../build/reference/section-specify-section-attributes.md) 选项的对齐参数修改特定节的对齐方式。  
  
 指定的对齐值不能小于最大的节对齐。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“命令行”**属性页。  
  
4.  将该选项键入**“附加选项”**框中。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)