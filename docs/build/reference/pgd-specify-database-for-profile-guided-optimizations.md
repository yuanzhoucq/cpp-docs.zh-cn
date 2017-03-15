---
title: "/PGD（为按配置文件优化指定数据库） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.ProfileGuidedDatabase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/PGD 链接器选项"
  - "-PGD 链接器选项"
ms.assetid: 9f312498-493b-461f-886f-92652257e443
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# /PGD（为按配置文件优化指定数据库）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

\/PGD:`filename`  
  
## 备注  
 其中：  
  
 `filename`  
 指定 .pgd 文件的名称，该文件将用于保存有关正在运行的程序的信息。  
  
## 备注  
 使用 [\/LTCG:PGINSTRUMENT](../../build/reference/ltcg-link-time-code-generation.md) 时，使用 \/PGD 为 .pgd 文件指定非默认名称或位置。  如果不指定 \/PGD，则 .pgd 文件名将与输出文件（.exe 或 .dll）的名称相同，并且将创建到与被调用链接相同的目录中。  
  
 使用 \/LTCG:PGOPTIMIZE 时，使用 \/PGD 指定用于创建优化映像的 .pgd 文件的名称。  
  
 有关更多信息，请参见[按配置优化](../../build/reference/profile-guided-optimizations.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  展开**“配置属性”**节点。  
  
3.  展开**“链接器”**节点。  
  
4.  选择**“优化”**属性页。  
  
5.  修改**“按配置优化数据库”**属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ProfileGuidedDatabase%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)