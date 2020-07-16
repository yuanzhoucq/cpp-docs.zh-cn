---
title: 链接器工具错误 LNK2038
ms.date: 12/15/2017
f1_keywords:
- LNK2038
helpviewer_keywords:
- LNK2038
ms.openlocfilehash: 69a832716dffee4e024b3bb1a1f0de6ee8105e99
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404159"
---
# <a name="linker-tools-error-lnk2038"></a>链接器工具错误 LNK2038

> 检测到 "*name*" 的不匹配项：值 "*value_1*" 与*文件名 .obj*中的值 "*value_2*" 不匹配

链接器检测到符号不匹配。 此错误表示应用程序的不同部分（包括库或应用程序链接到的其他对象代码）使用了冲突的符号定义。 [检测不匹配](../../preprocessor/detect-mismatch.md)杂注用于定义此类符号并检测它们的冲突值。

## <a name="possible-causes-and-solutions"></a>可能的原因和解决方法

当项目中的对象文件过时，可能会发生此错误。 在对此错误尝试其他解决方案之前，应执行清理生成以确保对象文件是最新的。

Visual Studio 定义以下符号以防止链接不兼容的代码，这种代码可能导致运行时错误或其他意外行为。

- `_MSC_VER`指示用于生成应用程序或库的 Microsoft c + + 编译器（MSVC）的主版本号和次版本号。 使用 MSVC 的一个版本编译的代码与使用具有不同主版本号和次版本号的版本编译的代码不兼容。 有关详细信息，请 `_MSC_VER` 参阅[预定义的宏](../../preprocessor/predefined-macros.md)。

   如果要链接到与你正在使用的 MSVC 版本不兼容的库，并且无法获取或生成兼容版本的库，则可以使用早期版本的编译器生成项目：将项目的 "**平台工具集**" 属性更改为先前的工具集。 有关详细信息，请参阅[如何：修改目标框架和平台工具集](../../build/how-to-modify-the-target-framework-and-platform-toolset.md)。

- `_ITERATOR_DEBUG_LEVEL`指示 c + + 标准库中启用的安全和调试功能的级别。 这些功能可更改某些 C++ 标准库对象的表示方式，从而使它们与使用不同的安全和调试功能的 C++ 标准库对象不兼容。 有关详细信息，请参阅 [_ITERATOR_DEBUG_LEVEL](../../standard-library/iterator-debug-level.md)。

- `RuntimeLibrary`指示应用程序或库使用的 c + + 标准库和 C 运行时的版本。 使用一个 C++ 标准库或 C 运行时版本的代码与使用另一个版本的代码的不兼容。 有关详细信息，请参阅 [/MD、/MT、/LD（使用运行时库）](../../build/reference/md-mt-ld-use-run-time-library.md)。

- `_PPLTASKS_WITH_WINRT`指示使用[并行模式库（PPL）](../../parallel/concrt/parallel-patterns-library-ppl.md)的代码链接到使用[/ZW](../../build/reference/zw-windows-runtime-compilation.md)编译器选项的其他设置编译的对象。 （**/ZW**支持 c + +/cx）使用或依赖于 PPL 的代码必须使用在应用程序的其余部分中使用的相同 **/ZW**设置来进行编译。

请确保这些符号的值在 Visual Studio 解决方案中的所有项目中是一致的，并确保这些值与应用程序链接到的代码和库是一致的。

## <a name="third-party-library-issues-and-vcpkg"></a>第三方库问题和 vcpkg

如果尝试在生成过程中配置第三方库时看到此错误，请考虑使用[vcpkg](../../vcpkg.md)（c + + 程序包管理器）安装和生成库。 vcpkg 支持较大和不断增长[的第三方库列表](https://github.com/Microsoft/vcpkg/tree/master/ports)，并将成功生成所需的所有配置属性和依赖项设置为项目的一部分。

## <a name="see-also"></a>另请参阅

[链接器工具错误和警告](../../error-messages/tool-errors/linker-tools-errors-and-warnings.md)
