---
title: "有关生成系统的更改 | Microsoft Docs"
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
  - "vc.msbuild.changes"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "生成系统更改, $(Inherit)"
  - "生成系统更改, $(NoInherit)"
  - "生成系统更改, .vsprops"
  - "生成系统更改, 自定义生成规则"
  - "生成系统更改, MSBuild"
  - "生成系统更改, 项目文件 (.vcxprog)"
  - "MSBuild, 生成系统更改"
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 有关生成系统的更改
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MSBuild系统是用来生成Visual C\+\+ 项目。  但是，在 Visual Studio 2008 和早期生成系统 VCBuild，使用了。  依赖 VCBuild 的某些文件类型和概念在当前不存在系统方式不同也不表示。  本文档讨论当前生成系统中的差异。  
  
## .vcproj 现在为 .vcxproj  
 项目文件不再使用 .vcproj 文件扩展名。  Visual Studio 会自动将在 Visual C\+\+ 早期版本中创建的项目文件转换为当前系统所用的格式。  有关如何手动升级项目的更多信息，请参见 [\/Upgrade](../Topic/-Upgrade%20\(devenv.exe\).md)。  
  
 在当前版本中，项目文件的文件扩展名为 .vcxproj。  
  
## .vsprops 现在为 .props  
 在早期版本中，项目属性表是具有 .vsprops 文件扩展名的、基于 XML 的文件。  使用项目属性表可以为生成工具（如编译器或链接器）指定开关并创建用户定义的宏。  
  
 在当前版本中，项目属性表的文件扩展名为 .props。  
  
## 自定义生成规则和 .rules 文件  
 在早期版本中，规则文件是具有 .rules 文件扩展名的、基于 XML 的文件。  利用规则文件，您可以定义自定义的生成规则，并将它们合并到 Visual C\+\+ 项目的生成过程中。  自定义的生成规则（可以与一个或多个文件扩展名关联）允许将输入文件传递给用于创建一个或多个输出文件的工具。  
  
 在此版本中，自定义生成规则可由 .xml、.props 和 .targets 这三种文件类型表示，而不是由 .rules 文件表示。   在将使用 Visual C\+\+ 早期版本创建的 .rules 文件迁移到当前版本时，将会创建等效的 .xml、.props 和 .targets 文件，并将它们与原始的 .rules 文件一起存储在项目中。  
  
> [!IMPORTANT]
>  在当前版本中，[!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] 不支持创建新规则。  因此，最简单的方法使用从创建使用 Visual C\+\+ 早期版本的项目的规则文件是将项目迁移到当前版本。  
  
## 继承宏  
 在早期版本中，**$\(Inherit\)** 宏指定在由项目生成系统撰写的命令行上显示继承属性所依据的顺序。  **$\(NoInherit\)** 宏会导致 $\(Inherit\) 的所有匹配项均被忽略且所有都应被继承的属性不被继承。  例如，在默认情况下，$\(Inherit\) 宏会导致通过使用 [\/I（其他包括目录）](../build/reference/i-additional-include-directories.md)编译器选项指定的文件追加到命令行。  
  
 在当前版本中，通过将属性的值指定为一个或多个文本值和属性宏的串联来支持继承。  不支持 **$\(Inherit\)** 和 **$\(NoInherit\)** 宏。  
  
 在下面的示例中，向属性页上的某个属性分配一个分号分隔的列表。  该列表由*\<value\>*属性值的`MyProperty`串联组成，该串联是通过使用宏表示法**$\(***MyProperty***\)**实现的。  
  
```  
Property=<value>;$(MyProperty)  
```  
  
## .vcxproj.user 文件  
 用户文件 \(.vcxproj.user\) 存储特定于用户的属性，例如调试和部署设置。  vcxproj.user 文件应用于特定用户的所有项目。  
  
## .vcxproj.filters 文件  
 当使用**解决方案资源管理器**向项目中添加文件时，筛选器文件 \(.vcxproj.filters\) 会基于该文件的文件扩展名定义在**解决方案资源管理器**树视图的哪个位置添加该文件。  
  
## VC\+\+ 目录设置  
 可在 [“VC\+\+ 目录”属性页](../ide/vcpp-directories-property-page.md)上指定 Visual C\+\+ 目录设置。  在 Visual Studio 早期版本中，目录设置按每个用户应用，并在 sysincl.dat 文件中指定排除目录的列表。  
  
 如果在命令行上运行 [devenv \/resetsettings](../Topic/-ResetSettings%20\(devenv.exe\).md)，则不能更改 VC\+\+ 目录设置。  如果您打开**“工具”**菜单，单击**“导入和导出设置”**，然后选择**“重置所有设置”**选项，则也不能更改这些设置。  
  
 从由 Visual C\+\+ 早期版本创建的 .vssettings 文件中迁移 VC\+\+ 目录设置。  打开**“工具”**菜单，单击**“导入和导出设置”**，选择**“导入选定的环境设置”**，然后按照向导中的说明操作。  或者，在您首次启动 Visual Studio 时，在**“选择默认环境设置”**对话框中，选择**“除了下面所选的默认设置以外，从早期版本中迁移并应用合格的设置”**。  
  
## 请参阅  
 [MSBuild \(Visual C\+\+\)](../build/msbuild-visual-cpp.md)