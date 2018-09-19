---
title: 链接器工具错误 LNK2038 |Microsoft Docs
ms.custom: ''
ms.date: 12/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2038
dev_langs:
- C++
helpviewer_keywords:
- LNK2038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 009644f18068454b0c765118b29c009cd33241a9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118110"
---
# <a name="linker-tools-error-lnk2038"></a>链接器工具错误 LNK2038

> 有关检测到不匹配*名称*： 值*value_1*不匹配值*value_2*' 中*filename.obj*

链接器检测到符号不匹配。 此错误表示应用程序，包括库或其他对象的不同部分代码应用的链接，使用冲突的符号定义。 [检测到不匹配](../../preprocessor/detect-mismatch.md)杂注用于定义此类符号和检测其冲突值。

## <a name="possible-causes-and-solutions"></a>可能的原因和解决方案

当项目中的对象文件过时，可能会发生此错误。 在对此错误尝试其他解决方案之前，应执行清理生成以确保对象文件是最新的。

Visual Studio 定义以下符号以防止链接不兼容的代码，这种代码可能导致运行时错误或其他意外行为。

- `_MSC_VER` 指示用于生成应用或库的 Visual c + + 编译器的主版本号和次版本号。 使用 Visual C++ 编译器编译的代码与使用具有不同的主版本号和次版本号的版本编译的代码不兼容。 有关详细信息，请参阅`_MSC_VER`中[预定义宏](../../preprocessor/predefined-macros.md)。

   如果要链接到与你使用，并且无法获取或生成兼容版本的库的 Visual c + + 编译器的版本不兼容的库，可以使用早期版本的编译器生成项目： 更改<c1/1>平台工具集**早期工具集的项目的属性。 有关详细信息，请参阅[如何： 修改目标框架和平台工具集](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

- `_ITERATOR_DEBUG_LEVEL` 指示级别的安全和调试 c + + 标准库中启用的功能。 这些功能可更改某些 C++ 标准库对象的表示方式，从而使它们与使用不同的安全和调试功能的 C++ 标准库对象不兼容。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)。

- `RuntimeLibrary` 指示由应用或库的 c + + 标准库和 C 运行时版本。 使用一个 C++ 标准库或 C 运行时版本的代码与使用另一个版本的代码的不兼容。 有关详细信息，请参阅 [/MD、/MT、/LD（使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)。

- `_PPLTASKS_WITH_WINRT` 表示使用该代码[并行模式库 (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)链接到使用不同的设置编译的对象[/ZW](../../build/reference/zw-windows-runtime-compilation.md)编译器选项。 (**/ZW**支持 C + + /cli CX。)使用或依赖于 PPL 的代码必须使用相同的编译 **/ZW**其余应用程序中使用的设置。

请确保这些符号的值在 Visual Studio 解决方案中的所有项目中是一致的，并确保这些值与应用程序链接到的代码和库是一致的。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 Vcpkg

如果尝试将第三方库配置为生成的一部分时看到此错误，请考虑使用[Vcpkg](../../vcpkg.md)，Visual c + + 包管理器，若要安装并生成库。 Vcpkg 支持大量且持续增长[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports)，并设置所有配置属性和依赖项所需的成功生成项目的一部分。 有关详细信息，请参阅相关[Visual c + + 博客](https://blogs.msdn.microsoft.com/vcblog/2016/09/19/vcpkg-a-tool-to-acquire-and-build-c-open-source-libraries-on-windows/)发布。

## <a name="see-also"></a>请参阅

[链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)