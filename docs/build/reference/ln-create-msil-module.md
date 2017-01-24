---
title: "/LN（创建 MSIL 模块） | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/LN"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/LN 编译器选项 [C++]"
  - "-LN 编译器选项 [C++]"
ms.assetid: 4f38f4f4-3176-4caf-8200-5c7585dc1ed3
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /LN（创建 MSIL 模块）
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指定程序集清单不应插入到输出文件中。  
  
## 语法  
  
```  
/LN  
```  
  
## 备注  
 默认情况下，**\/LN** 无效（将程序集清单插入到输出文件中）。  
  
 当使用 **\/LN** 时，必须同时使用 [\/clr（公共语言运行时编译）](../../build/reference/clr-common-language-runtime-compilation.md) 选项之一。  
  
 清单中不具有程序集元数据的托管程序称作模块。  如果用 [\/c（在不链接的情况下进行编译）](../../build/reference/c-compile-without-linking.md) 和 **\/LN** 进行编译，请在链接器阶段指定 [\/NOASSEMBLY（创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md) 以创建输出文件。  
  
 如果希望采用基于组件的方法来生成程序集，则可能需要创建模块。即，可以创作类型并将其编译进模块中。然后，您可以从一个或多个模块生成程序集。有关从模块创建程序集的更多信息，请参见 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md) 或 [Al.exe（程序集链接器）](../Topic/Al.exe%20\(Assembly%20Linker\).md)。  
  
 代码模块的默认文件扩展名为 .netmodule。  
  
 在 Visual C\+\+ 2005 之前的 [!INCLUDE[vcprvc](../../build/includes/vcprvc_md.md)] 版本中，使用 **\/clr:noAssembly** 创建模块。  
  
 Visual C\+\+ 链接器接受 .netmodule 文件，因为输入和链接器生成的输出文件是程序集还是 .netmodule 不在输入到链接器的运行时关联任何 .netmodules。有关详细信息，请参阅[用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)。  
  
### 在 Visual Studio 开发环境中设置此编译器选项  
  
-   在链接器阶段指定 [\/NOASSEMBLY（创建 MSIL 模块）](../../build/reference/noassembly-create-a-msil-module.md) 以创建输出文件。  
  
### 以编程方式设置此编译器选项  
  
-   不能以编程方式更改此编译器选项。  
  
## 请参阅  
 [编译器选项](../../build/reference/compiler-options.md)   
 [设置编译器选项](../../build/reference/setting-compiler-options.md)