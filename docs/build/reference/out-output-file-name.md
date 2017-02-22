---
title: "/OUT（输出文件名） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.OutputFile"
  - "/out"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/OUT C++ 链接器选项"
  - "链接器 [C++], 输出文件"
  - "OUT 链接器选项"
  - "-OUT 链接器选项"
  - "输出文件, 名称链接器选项"
ms.assetid: 976210a4-e51f-4cfb-af5e-c16344455834
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# /OUT（输出文件名）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/OUT:filename  
```  
  
## 备注  
 其中：  
  
 *filename*  
 用户指定的输出文件名。  该名称将会替换默认名称。  
  
## 备注  
 \/OUT 选项重写链接器创建的程序的默认名称和位置。  
  
 默认情况下，链接器用指定的第一个 .obj 文件的基名称和适当的扩展名（.exe 或 .dll）来组成文件名。  
  
 该选项设置 .mapfile 或导入库的默认基名称。  有关详细信息，请参见[生成映射文件](../../build/reference/map-generate-mapfile.md) \(\/MAP\) 和 [\/IMPLIB](../../build/reference/implib-name-import-library.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“常规”属性页。  
  
4.  修改“输出文件”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)