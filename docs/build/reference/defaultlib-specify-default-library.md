---
title: "/DEFAULTLIB（指定默认库） | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VC.Project.VCLinkerTool.DefaultLibraries"
  - "/defaultlib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DEFAULTLIB 链接器选项"
  - "DEFAULTLIB 链接器选项"
  - "-DEFAULTLIB 链接器选项"
  - "库, 添加到列表"
ms.assetid: 6af7ff49-c170-4a13-97e2-2b9ae2de20c9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# /DEFAULTLIB（指定默认库）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/DEFAULTLIB:library  
```  
  
## 备注  
 其中：  
  
 *library*  
 解析外部引用时搜索的库名。  
  
## 备注  
 \/DEFAULTLIB 选项将一个 *library* 添加到 LINK 在解析引用时搜索的库列表。  用 \/DEFAULTLIB 指定的库在命令行上指定的库之后和 .obj 文件中指定的默认库之前被搜索。  
  
 [忽略所有默认库](../../build/reference/nodefaultlib-ignore-libraries.md) \(\/NODEFAULTLIB\) 选项重写 \/DEFAULTLIB:*library*。  如果在两者中指定了相同的 *library* 名称，[忽略库](../../build/reference/nodefaultlib-ignore-libraries.md) \(\/NODEFAULTLIB:*library*\) 选项将重写 \/DEFAULTLIB:*library*。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
-   此链接器选项在 Visual Studio 开发环境中不可用。  若要将库添加到链接阶段，请使用**“输入”**属性页中的**“附加依赖项”**属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)