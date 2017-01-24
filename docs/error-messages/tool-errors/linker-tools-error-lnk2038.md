---
title: "链接器工具错误 LNK2038 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2038"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2038"
ms.assetid: b8d0fb35-eee6-4f52-b3c4-239cb4f65656
caps.latest.revision: 13
caps.handback.revision: 13
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 链接器工具错误 LNK2038
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

检测到 '\<name\>'不匹配：'\<value 1\>' 值与\<filename.obj\>中的 '\<value 2\>' 值不匹配  
  
 链接器检测到符号不匹配。  此错误指示应用不同部分的，包括库或其他应用程序链接于使用符号的冲突定义的对象代码。  [检测不匹配](../../preprocessor/detect-mismatch.md) 编译指示用于定义符号和检测这些冲突的值。  
  
### 更正此错误  
  
-   当项目的对象文件已过时，可能会发生此错误。  在尝试该错误的其他解决方案之前，应执行清理生成确保对象文件是当前文件。  
  
-   Visual Studio 定义以下符号防止链接不兼容的代码，这可能导致运行时错误或其他意外行为。  
  
     `_MSC_VER`  
     指示用于构造应用程序或库的 Visual C\+\+ 编译器的主版本号和次版本号。  代码编译使用 Visual C\+\+ 编译器的一个版本，它与使用具有不同的主版本号和次版本号版本编译的代码不兼容。  有关更多信息，请参见[预定义的宏](../../preprocessor/predefined-macros.md)中的 `_MSC_VER`。  
  
     如果链接的库与您使用的 Visual C\+\+ 编译器版本不兼容，您无法获取或生成库的兼容版本。可以使用编译器早期版本生成项目，更改项目的 **平台工具集** 属性。  有关详细信息，请参阅[如何：修改目标框架和平台工具集](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)。  
  
     `_ITERATOR_DEBUG_LEVEL`  
     指示在 C\+\+ 标准库中启用的安全级别和调试功能。  这些功能可以更改特定的 C\+\+ 标准库对象的表示，从而使它们与使用不同的安全性和调试功能的功能不兼容。  有关详细信息，请参阅[\_ITERATOR\_DEBUG\_LEVEL](../../standard-library/iterator-debug-level.md)。  
  
     `RuntimeLibrary`  
     指示应用程序或库使用的 C\+\+ 标准库和 C 运行时版本。  代码使用 C\+\+ 标准库或 C 运行时的一个版本，它与使用不同版本的代码不兼容。  有关详细信息，请参阅[\/MD、\/MT、\/LD（使用运行库）](../../build/reference/md-mt-ld-use-run-time-library.md)。  
  
     `_PPLTASKS_WITH_WINRT`  
     指示使用[Parallel Patterns Library \(PPL\)](../../parallel/concrt/parallel-patterns-library-ppl.md) 的代码链接到使用不同设置编译的用于[\/ZW](../../build/reference/zw-windows-runtime-compilation.md) 编译器选项的对象。\(**\/ZW** 支持 C\+\+\/CX。\)使用或依赖于 PPL 的代码必须使用相同的**\/ZW** 在应用程序静止时使用的设置编译。  
  
     确保这些符号的值是一致的，在 Visual Studio 解决方案的项目中，它们与应用程序链接的代码和库是一致的。  
  
## 请参阅  
 [链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)