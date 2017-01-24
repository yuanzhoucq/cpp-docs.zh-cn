---
title: "如何：从现有 .Cto 文件创建 .Vsct 文件 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSCT 文件, 基于 .cto 文件创建"
ms.assetid: 847717c9-477d-4ac9-8b2c-2da878912478
caps.latest.revision: 11
caps.handback.revision: 11
manager: "douge"
---
# 如何：从现有 .Cto 文件创建 .Vsct 文件
可从现有的二进制 .cto 文件创建一个基于 XML 的 .vsct 文件。 这样既可充分利用新的命令表编译器格式。 即使 .cto 文件是从 .ctc 文件编译而来，此过程仍然有效。 你可以编辑 .vsct 文件并将其编译到其他 .cto 文件。  
  
### 从 .cto 文件创建 .Vsct 文件  
  
1.  获取 .cto 文件及其对应 .ctsym 文件的副本。  
  
2.  将文件与 vsct.exe 编译器放在同一目录中。  
  
3.  在 Visual Studio 命令提示符处，转到包含 .cto 和 .ctsym 文件的目录。  
  
4.  类型 **vsct.exe** *ctofilename***.cto** *vsctfilename***.vsct \-S***symfilename***.ctsym**。  
  
     `ctofilename` 是 .cto 文件的名称，`vsctfilename` 是要创建的 vsct 文件的名称，而 `symfilename` 是 .ctsym 文件的名称。  
  
     此过程可创建新的 .vsct XML 命令表编译器文件。 可像任何其他 .vsct 文件一样，使用 vsct.exe（vsct 编译器）来编辑和编译此文件。  
  
## 请参阅  
 [如何: 创建。Vsct 文件](../Topic/How%20to:%20Create%20a%20.Vsct%20File.md)   
 [Visual Studio 命令表 \(。Vsct\) 文件](../Topic/Visual%20Studio%20Command%20Table%20\(.Vsct\)%20Files.md)