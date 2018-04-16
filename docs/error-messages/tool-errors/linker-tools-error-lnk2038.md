---
title: "链接器工具错误 LNK2038 |Microsoft 文档"
ms.custom: 
ms.date: 12/15/2017
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2038
dev_langs:
- C++
helpviewer_keywords:
- LNK2038
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 13f65f403cac43551b787abab15713fb9ffab618
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2018
---
# <a name="linker-tools-error-lnk2038"></a>链接器工具错误 LNK2038

> 有关检测到不匹配*名称*： 值*value_1*不匹配值*value_2*中*.o b j*

链接器检测到符号不匹配。 此错误指示不同部分的应用程序，包括库或其他对象代码的应用程序链接，使用冲突的符号定义。 [检测到不匹配](../../preprocessor/detect-mismatch.md)杂注用于定义此类符号和检测其冲突值。

## <a name="possible-causes-and-solutions"></a>可能的原因和解决方案

当项目中的对象文件过时，可能会发生此错误。 在对此错误尝试其他解决方案之前，应执行清理生成以确保对象文件是最新的。

Visual Studio 定义以下符号以防止链接不兼容的代码，这种代码可能导致运行时错误或其他意外行为。

- `_MSC_VER`  
   指示用于构造应用程序或库的 Visual C++ 编译器的主版本号和次版本号。 使用 Visual C++ 编译器编译的代码与使用具有不同的主版本号和次版本号的版本编译的代码不兼容。 有关详细信息，请参阅`_MSC_VER`中[预定义的宏](../../preprocessor/predefined-macros.md)。

   如果要链接到与你使用的并且无法获取或生成兼容版本的库的 Visual c + + 编译器的版本不兼容的库，可以使用早期版本的编译器来生成你的项目： 更改<c1/1>平台工具集**项目到更早版本的工具集的属性。 有关详细信息，请参阅[如何： 修改目标框架和平台工具集](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

- `_ITERATOR_DEBUG_LEVEL`  
   指示在 C++ 标准库中启用的安全和调试功能的级别。 这些功能可更改某些 C++ 标准库对象的表示方式，从而使它们与使用不同的安全和调试功能的 C++ 标准库对象不兼容。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)。

- `RuntimeLibrary`  
   指示应用程序或库使用的 C++ 标准库和 C 运行时的版本。 使用一个 C++ 标准库或 C 运行时版本的代码与使用另一个版本的代码的不兼容。 有关详细信息，请参阅 [/MD、/MT、/LD（使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)。

- `_PPLTASKS_WITH_WINRT`  
   指示使用该代码[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)链接到对象使用的其他设置编译的[/ZW](../../build/reference/zw-windows-runtime-compilation.md)编译器选项。 (**/ZW**支持 C + + /cli CX。)使用或依赖于 PPL 的代码必须使用相同的编译**/ZW**在其余应用程序中使用的设置。

请确保这些符号的值在 Visual Studio 解决方案中的所有项目中是一致的，并确保这些值与应用程序链接到的代码和库是一致的。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 Vcpkg

如果你尝试将第三方库配置为生成的一部分时，你会看到此错误，请考虑使用[Vcpkg](../../vcpkg.md)，Visual c + + 包管理器中，若要安装和构建的库。 大型以及不断增长的 Vcpkg 支持[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports)，并将设置所有配置属性和所需的成功生成你的项目的一部分的依赖项。 有关详细信息，请参阅相关[Visual c + + 博客](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)文章。

## <a name="see-also"></a>请参阅

[链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)