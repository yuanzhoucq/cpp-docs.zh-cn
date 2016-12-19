---
title: "/LIBPATH（附加的 Libpath） | Microsoft Docs"
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
  - "/libpath"
  - "VC.Project.VCLinkerTool.AdditionalLibraryDirectories"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LIBPATH 链接器选项"
  - "“附加的 Libpath”链接器选项"
  - "环境库路径重写"
  - "LIBPATH 链接器选项"
  - "-LIBPATH 链接器选项"
  - "库路径链接器选项"
ms.assetid: 7240af0b-9a3d-4d53-8169-2a92cd6958ba
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LIBPATH（附加的 Libpath）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/LIBPATH:dir  
```  
  
## 备注  
 其中：  
  
 `dir`  
 在链接器搜索 LIB 环境选项中指定的路径之前，指定它将要搜索的路径。  
  
## 备注  
 使用 \/LIBPATH 选项重写环境库路径。  链接器将首先在该选项所指定的路径中搜索，然后在 LIB 环境变量中所指定的路径中搜索。  对于您输入的每个 \/LIBPATH 选项，只能指定一个目录。  如果要指定一个以上的目录，则必须指定多个 \/LIBPATH 选项。  链接器然后将按顺序搜索指定的目录。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“常规”属性页。  
  
4.  修改“附加库目录”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalLibraryDirectories%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)