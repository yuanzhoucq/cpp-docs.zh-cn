---
title: "选择 .netmodule 输入文件的格式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 选择 .netmodule 输入文件的格式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

MSIL .obj 文件（用 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 编译）也可用作.netmodule文件 ..obj 文件包含元数据和本机符号。.netmodules 只包含元数据。  
  
 可通过 \/addmodule 编译器选项将 MSIL .obj 文件传递给任何其他 Visual Studio 编译器（但需注意，该 .obj 文件将成为结果程序集的一部分，而且必须随程序集一起提供）。例如，Visual C\# 和 Visual Basic 具有 \/addmodule 编译器选项。  
  
> [!NOTE]
>  大多数情况下，需要向链接器传递创建.net模块的编译器的.obj文件 .这一点的一个例外是如果创建具有[\/clr:pure](../../build/reference/clr-common-language-runtime-compilation.md) 的.netmodule。将 .dll 或 .netmodule MSIL 模块文件到链接器会导致 LNK1107。  
  
 .obj 文件，及其关联 .h 文件时，通过在源中的 \#include C\+\+ 引用，允许应用程序使用本机类型，.netmodule 文件，因此，只有模块，而在托管类型可以由 C.C\+\+ 应用程序。如果尝试向 \#using 传递 .obj 文件，则关于本机类型的信息将不可用；改为 \#include 此 .obj 文件的 .h 文件。  
  
 其他 Visual Studio 编译器只可以使用模块中的托管类型。  
  
 使用下确定是否使用需要 .netmodule 或作为模块的 .obj 文件输入到 Visual C\+\+ 链接器：  
  
-   除了 Visual C\+\+ 外，如果您生成使用 Visual Studio 编译器，请生成 .netmodule .netmodule 并使用作为输入传递给链接器。  
  
-   如果使用 Visual C\+\+ 编译器生成模块，并且模块将用于生成库以外的某些内容，则使用编译器生成的 .obj 文件作为链接器的模块输入，而不要将.netmodule文件作为输入.  
  
-   如果模块将用于生成一个本机库（而不是托管库），则使用 .obj 文件作为链接器的模块输入并生成一个 .lib 库文件。  
  
-   如果模块将用于生成托管库，并且链接器的所有模块输入将都是可验证的（使用 \/clr:safe 生成），则使用 .obj 文件作为链接器的模块输入并生成一个 .dll（程序集）或 .netmodule \(模块\)库文件.  
  
-   如果模块用于构造宿主的库，并且，如果为，链接器的模块项将导致与 \/clr:pure 或 \/clr:safe，请使用链接器输入的 .obj 文件作为模块并生成程序集 \(.dll\) 或 .netmodule \(模块 \)，如果您只想从公开库的托管类型。如果要公开库中的托管类型，并且还要 C\+\+ 应用程序使用库中的本机类型，则库将由库组件模块的 .obj 文件组成（您还要提供各个模块的 .h 文件，以便可以使用源代码中的 \#include 引用它们）。  
  
-   如果模块将用于生成托管库，并且链接器的一个或多个模块输入将仅用 \/clr 生成，则使用 .obj 文件作为链接器的模块输入并生成一个 .dll（程序集）。如果要公开库中的托管类型，并且还要 C\+\+ 应用程序使用库中的本机类型，则库将由库组件模块的 .obj 文件组成（您还要提供各个模块的 .h 文件，以便可以使用源代码中的 \#include 引用它们）。  
  
## 请参阅  
 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)