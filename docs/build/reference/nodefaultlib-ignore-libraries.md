---
title: "/NODEFAULTLIB（忽略库） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.IgnoreAllDefaultLibraries"
  - "VC.Project.VCLinkerTool.IgnoreDefaultLibraryNames"
  - "/nodefaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/NODEFAULTLIB 链接器选项"
  - "默认库, 移除"
  - "忽略库链接器选项"
  - "库, 忽略"
  - "NODEFAULTLIB 链接器选项"
  - "-NODEFAULTLIB 链接器选项"
ms.assetid: 7270b673-6711-468e-97a7-c2925ac2be6e
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# /NODEFAULTLIB（忽略库）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/NODEFAULTLIB[:library]   
```  
  
## 备注  
 其中：  
  
 *library*  
 当链接器解析外部引用时使链接器忽略的库。  
  
## 备注  
 \/NODEFAULTLIB 选项通知链接器从其在解析外部引用时搜索的库列表中移除一个或多个默认库。  
  
 要创建一个不包含默认库引用的 .obj 文件，请使用 [\/Zl（省略默认库名）](../../build/reference/zl-omit-default-library-name.md)。  
  
 默认情况下，\/NODEFAULTLIB 从它解析外部引用时所搜索的库列表中移除所有默认库。  可选 *library* 参数使您得以将指定的库从它解析外部引用时所搜索的库列表中移除。  为每个要排除的库指定一个 \/NODEFAULTLIB 选项。  
  
 链接器解析外部定义的引用时，首先通过在您显式指定的库中搜索，然后在用 \/DEFAULTLIB 选项指定的默认库中搜索，最后在 .obj 文件中命名的默认库中搜索。  
  
 \/NODEFAULTLIB:*library* 重写 [\/DEFAULTLIB:](../../build/reference/defaultlib-specify-default-library.md) *library*（如果在这两者中指定相同的 *library* 名称）。  
  
 例如，如果在没有 C 运行库情况下使用 \/NODEFAULTLIB 生成程序，可能还需要使用 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 指定程序中的入口点（函数）。  有关详细信息，请参阅[CRT 库功能](../../c-runtime-library/crt-library-features.md)。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击**“输入”**属性页。  
  
4.  选择**“忽略所有默认库”**属性或在**“忽略指定库”**属性中指定要忽略的库列表。  **“命令行”**属性页将显示对这些属性所做的更改的效果。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreDefaultLibraryNames%2A>和<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.IgnoreAllDefaultLibraries%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)