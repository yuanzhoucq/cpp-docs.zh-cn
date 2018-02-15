---
title: "选择的.netmodule 格式输入文件 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6b83039a054e19e62cbbe87befbe08dd7997e51
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/14/2018
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>选择 .netmodule 输入文件的格式
MSIL 的.obj 文件 (使用编译[/clr](../../build/reference/clr-common-language-runtime-compilation.md)) 还可用作.netmodule 文件。  .obj 文件包含元数据和本机符号。  .netmodule 只包含元数据。  
  
 你可以通过 /addmodule 编译器选项将 MSIL 的.obj 文件传递给任何其他 Visual Studio 编译器 （但请注意，.obj 文件将成为生成的程序集的一部分，并且必须随程序集）。  例如，Visual C# 和 Visual Basic 有 /addmodule 编译器选项。  
  
> [!NOTE]
>  大多数情况下，您需要从创建 .net 模块的编译中向链接器传递 .obj 文件。  将 .dll 或 .netmodule MSIL 模块文件传递到链接器可能导致 LNK1107。  
  
 通过源中的 #include 引用的 .obj 文件及其关联的 .h 文件允许 C++ 应用程序使用模块中的本机类型，而在 .netmodule 文件中，只有托管类型可由 C++ 应用程序使用。  如果你尝试传递的.obj 文件，以便 #using，有关本机类型的信息将不可用;# 改为 include.obj 文件的.h 文件。  
  
 其他 Visual Studio 编译器只能使用从某一模块的托管的类型。  
  
 请使用以下内容确定是否需要使用 .netmodule 或 .obj 文件作为 Visual C++ 链接器的模块输入：  
  
-   如果您要使用 Visual C++ 之外的 Visual Studio 编译器进行构建，请生成 .netmodule 并使用它作为链接器的输入。  
  
-   如果要使用 Visual C++ 编译器生成模块，并且该模块将用于构建库以外的内容，则使用编译器生成的 .obj 文件作为链接器的模块输入；不要使用 .netmodule 文件作为输入。  
  
-   如果你的模块将用于构建本机 （而不是托管） 库，使用作为模块链接器输入的.obj 文件，并生成.lib 库文件。  
  
-   如果模块将用于构建托管库，并且链接器的所有模块输入都是可验证的（使用 /clr:safe 生成），则使用 .obj 文件作为链接器的模块输入并生成 .dll（程序集）或 .netmodule（模块）库文件。  
  
-   如果模块将用于构建的托管的库，并且仅用 /clr 生成则不会产生链接器的一个或多个模块输入，使用作为模块链接器输入的.obj 文件，并生成.dll （程序集）。  如果你想要公开库中的托管的类型，并且如果还想 c + + 应用程序使用库中的本机类型，你的库将包含 （你将还需要每个模块的.h 文件的库组件模块的.obj 文件以便它们可引用使用 #include 源代码中的代码)。  
  
## <a name="see-also"></a>请参阅  
 [用作链接器输入的 .netmodule 文件](../../build/reference/netmodule-files-as-linker-input.md)