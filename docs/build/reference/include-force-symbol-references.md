---
title: "/INCLUDE（强制符号引用） | Microsoft Docs"
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
  - "/include"
  - "VC.Project.VCLinkerTool.ForceSymbolReferences"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/INCLUDE 链接器选项"
  - "强制符号引用链接器选项"
  - "INCLUDE 链接器选项"
  - "-INCLUDE 链接器选项"
  - "符号引用链接器强制"
  - "symbols, 添加到符号表"
ms.assetid: 4a039677-360a-480f-bd0b-448e239b449c
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /INCLUDE（强制符号引用）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

```  
/INCLUDE:symbol  
```  
  
## 备注  
 其中：  
  
 `symbol`  
 指定要添加到符号表的符号。  
  
## 备注  
 \/INCLUDE 选项告知链接器将指定的符号添加到符号表中。  
  
 若要指定多个符号，请在符号名称之间键入逗号 \(,\)、分号 \(;\) 或空格。  在命令行上，对每个符号指定一次 \/INCLUDE:`symbol`。  
  
 链接器通过将包含符号定义的对象添加到程序来解析 `symbol`。  该功能对于添包含不会链接到程序的库对象非常有用。  
  
 用该选项指定符号将通过 [\/OPT:REF](../../build/reference/opt-optimizations.md) 重写该符号的移除。  
  
### 在 Visual Studio 开发环境中设置此链接器选项  
  
1.  打开项目的**“属性页”**对话框。  有关详细信息，请参见[设置 Visual C\+\+ 项目属性](../../ide/working-with-project-properties.md)。  
  
2.  单击“链接器”文件夹。  
  
3.  单击“输入”属性页。  
  
4.  修改“强制符号引用”属性。  
  
### 以编程方式设置此链接器选项  
  
-   请参见<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ForceSymbolReferences%2A>。  
  
## 请参阅  
 [设置链接器选项](../../build/reference/setting-linker-options.md)   
 [链接器选项](../../build/reference/linker-options.md)