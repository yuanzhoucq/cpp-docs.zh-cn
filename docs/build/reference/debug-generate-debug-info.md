---
title: "/DEBUG（生成调试信息） | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.GenerateDebugInformation"
  - "/debug"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 文件, 生成调试信息"
  - "/DEBUG 链接器选项"
  - "DEBUG 链接器选项"
  - "-DEBUG 链接器选项"
  - "调试 [C++], 调试信息文件"
  - "调试 [C++], 链接器选项"
  - "生成调试信息链接器选项"
  - "PDB 文件"
  - "pdb 文件, 生成调试信息"
  - "程序数据库 [C++]"
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
caps.latest.revision: 11
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DEBUG（生成调试信息）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEBUG  
```  
  
## 备注  
 \/DEBUG 选项可为 .exe 文件或 DLL 创建调试信息。  
  
 链接器将调试信息放在程序数据库 \(PDB\) 中。  它在后面的程序生成期间更新 PDB。  
  
 为调试创建的 .exe 文件或 DLL 包含相应 PDB 的名称和路径。  调试器在您调试程序时读取嵌入的名称并使用 PDB。  链接器使用程序的基名称和扩展名 .pdb 命名程序数据库，并嵌入它的创建路径。  若要重写该默认值，请设置 [\/PDB](../../build/reference/pdb-use-program-database.md) 并指定不同的文件名。  
  
 编译器的[仅限行号](../../build/reference/z7-zi-zi-debug-information-format.md) \(\/Zd\) 或 [C7 兼容](../../build/reference/z7-zi-zi-debug-information-format.md) \(\/Z7\) 选项使编译器将调试信息保留在 .obj 文件中。  还可以使用[程序数据库](../../build/reference/z7-zi-zi-debug-information-format.md) \(\/Zi\) 编译器选项将调试信息存储在 .obj 文件的 PDB 中。  链接器首先在写入 .obj 文件的绝对路径中查找对象的 PDB，然后在包含 .obj 文件的目录中查找。  不能指定对象的 PDB 文件名或链接器的位置。  
  
 指定 \/DEBUG 时暗含 [\/INCREMENTAL](../../build/reference/incremental-link-incrementally.md)。  
  
 \/DEBUG 将 [\/OPT](../../build/reference/opt-optimizations.md) 选项的默认值从 REF 更改为 NOREF 以及从 ICF 更改为 NOICF（因此，需要显式指定 \/OPT:REF 或 \/OPT:ICF）。  
  
 有关 .PDB 和 .DBG 文件的更多信息，请参见知识库文章 Q121366，INFO: PDB and DBG Files \- What They Are and How They Work。  可在 MSDN 库 或 [http:\/\/search.support.microsoft.com](http://support.microsoft.com/) 上找到知识库文章。  
  
 无法创建包含调试信息的 .exe 或 .dll。  调试信息始终放在 .pdb 文件中。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“调试”**属性页。  
  
4.  修改“生成调试信息”属性。  
  
### 以编程方式设置此链接器选项  
  
1.  请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)