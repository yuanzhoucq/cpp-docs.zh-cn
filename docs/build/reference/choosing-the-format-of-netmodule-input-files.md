---
title: 选择 .netmodule 输入文件的格式
ms.date: 11/04/2016
ms.assetid: 4653d1bd-300f-4083-86f5-d1a06f44e61c
ms.openlocfilehash: b4d4b80e4b9195d184b9d97cea67bbaaa3d7d843
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81320563"
---
# <a name="choosing-the-format-of-netmodule-input-files"></a>选择 .netmodule 输入文件的格式

MSIL .obj 文件（使用[/clr](clr-common-language-runtime-compilation.md)编译）也可以用作 .netmodule 文件。  .obj 文件包含元数据和本机符号。  .netmodule 只包含元数据。

您可以通过 /addmodule 编译器选项将 MSIL .obj 文件传递给任何其他 Visual Studio 编译器（但请注意，.obj 文件将成为生成的程序集的一部分，并且必须随程序集一起提供）。  例如，Visual C++ 和可视化基本具有 /addmodule 编译器选项。

> [!NOTE]
> 大多数情况下，您需要从创建 .net 模块的编译中向链接器传递 .obj 文件。  将 .dll 或 .netmodule MSIL 模块文件传递到链接器可能导致 LNK1107。

通过源中的 #include 引用的 .obj 文件及其关联的 .h 文件允许 C++ 应用程序使用模块中的本机类型，而在 .netmodule 文件中，只有托管类型可由 C++ 应用程序使用。  如果尝试将 .obj 文件传递给#using，则有关本机类型的信息将不可用;因此，将不可用。#include .obj 文件的 .h 文件。

其他 Visual Studio 编译器只能使用模块中的托管类型。

使用以下内容确定是否需要使用 .netmodule 还是 .obj 文件作为 MSVC 链接器的模块输入：

- 如果您要使用 Visual C++ 之外的 Visual Studio 编译器进行构建，请生成 .netmodule 并使用它作为链接器的输入。

- 如果使用 MSVC 编译器生成模块，并且模块将用于构建库以外的内容，请使用编译器生成的 .obj 文件作为模块输入链接器;不要使用 .netmodule 文件作为输入。

- 如果模块将用于构建本机（非托管）库，请使用 .obj 文件作为链接器的模块输入并生成 .lib 库文件。

- 如果模块将用于构建托管库，并且链接器的所有模块输入都是可验证的（使用 /clr:safe 生成），则使用 .obj 文件作为链接器的模块输入并生成 .dll（程序集）或 .netmodule（模块）库文件。

- 如果您的模块将用于构建托管库，并且如果只需 /clr 即可生成一个或多个输入链接器的模块，请使用 .obj 文件作为链接器的模块输入并生成 .dll（程序集）。  如果要从库中公开托管类型，并且还希望C++应用程序在库中使用本机类型，则库将由库组件模块的 .obj 文件组成（您还需要为每个模块提供 .h 文件，以便可以使用源代码中#include引用这些文件）。

## <a name="see-also"></a>另请参阅

[用作链接器输入的 .netmodule 文件](netmodule-files-as-linker-input.md)
