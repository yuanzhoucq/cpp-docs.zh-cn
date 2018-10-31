---
title: 链接器工具错误 LNK2005 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2005
dev_langs:
- C++
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8a3dbb1d63e7d7c6f5e036fc0cde967277c91a40
ms.sourcegitcommit: d3c41b16bf05af2149090e996d8e71cd6cd55c7a
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/09/2018
ms.locfileid: "48890115"
---
# <a name="linker-tools-error-lnk2005"></a>链接器工具错误 LNK2005

> *符号*对象中已定义

符号*符号*已多次定义。

此错误后跟错误[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。

### <a name="possible-causes-and-solutions"></a>可能的原因和解决方案

通常情况下，此错误意味着必须要断开*定义的一个规则*，这允许跨整个可执行文件只有一个定义为任何使用的模板、 函数、 类型或对象在给定的对象文件中，并只有一个定义外部可见的对象或函数。

以下是此错误的一些常见原因。

- 当标头文件定义一个变量时，可以发生此错误。 例如，如果在项目中，在多个源文件中包含此标头文件，则会发生错误：

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   可能的解决方案包括：

   - 将变量声明`extern`标头文件中： `extern int global_int;`，然后将它定义并根据需要对其有且只有一个源文件中进行初始化： `int global_int = 17;`。 此变量现在是一个全局，您可以使用任何源文件中通过声明它`extern`，例如，通过包括标头文件。 我们建议针对变量必须是全局的此解决方案，但良好的软件工程实践最大程度减少全局变量。

   - 将变量声明[静态](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`。 这将限制到当前的对象文件中，定义的作用域，并允许多个对象文件有其自己的变量副本。 我们不建议你定义标头文件中可能出现的混淆的全局变量由于静态变量。 更喜欢将静态变量的定义移到使用它们的源文件。

   - 将变量声明[selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`。 这将告知链接器通过所有外部引用中选取一个定义，以便使用并丢弃其余部分。 合并的导入库时，此解决方案是有时很有用。 否则，我们不建议这样做作为一种方法，以避免链接器错误。

- 当标头文件定义不是一个函数时，会出现此错误`inline`。 如果在多个源文件中包括此标头文件，您可执行文件中获取多个定义的函数。

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   可能的解决方案包括：

   - 添加`inline`函数的关键字：

        ```h
        // LNK2005_func_inline.h
        inline int sample_function(int k) { return 42 * (k % 167); }
        ```

   - 删除标头文件中的函数体并保留仅声明，然后实现一个且只有一个源文件中的函数：

        ```h
        // LNK2005_func_decl.h
        int sample_function(int);
        ```

        ```cpp
        // LNK2005_func_impl.cpp
        int sample_function(int k) { return 42 * (k % 167); }
        ```

- 如果在标头文件中定义类声明的外部的成员函数，也可能发生此错误：

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   若要解决此问题，将在类中的成员函数定义。 在类声明中定义的成员函数进行了隐式内联。

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- 如果链接多个 CRT 的标准库的版本，可以发生此错误。 例如，如果尝试链接到可执行文件的同时零售和调试 CRT 库或库的静态和动态版本或标准库的两个不同版本，可能会报告此错误很多时候。 若要解决此问题，请从链接命令删除每个库的所有只保留一个的副本。 我们不建议您混用零售和调试库或库，在同一可执行文件中的不同版本。

   若要告知链接器命令行上使用非默认值，指定要使用，并使用的库[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)选项来禁用默认库。 在 IDE 中，向项目添加引用你指定的库以使用，然后打开**属性页**用于你的项目，并在对话框**链接器**，**输入**属性页上，设置**忽略所有默认库**，或**忽略特定默认库**属性禁用默认库。

- 如果当你使用混合使用静态和动态库，可能出现此错误[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项。 例如，如果使用的 DLL 中生成可执行文件中的静态 CRT 的该链接，可以发生此错误。 若要解决此问题，请使用仅静态库或仅动态库整个可执行文件和生成要在可执行文件中使用任何库。

- 如果符号为封装的函数可能出现此错误 (使用编译时所创建[/Gy](../../build/reference/gy-enable-function-level-linking.md)) 和它包含在多个文件，但在各编译间已改变。 若要解决此问题，请重新编译包含封装的函数的所有文件。

- 如果在不同的库中的两个成员对象中以不同的方式定义了符号，并且使用这两个成员对象，可以发生此错误。 若要解决此问题时静态链接库的一种方法是使用成员对象中只有一个库，并将该库首先包含链接器命令行上。 若要使用这两个符号，必须创建一种方法来区分它们。 例如，如果可以生成源的库，可以包装在唯一的命名空间中的每个库。 或者，可以创建新的包装库，它使用唯一名称来包装对原始库之一的引用，将新的库链接到原始的库，然后链接到新库而不是原始的库的可执行文件。

- 如果可能发生此错误`extern const`变量定义了两次，并在每个定义中具有不同的值。 若要解决此问题，定义常量的唯一一次，或使用命名空间或`enum class`要区分这些常量定义。

- 如果您将 uuid.lib 与定义 Guid （例如 oledb.lib 和 adsiid.lib） 其他.lib 文件，可以发生此错误。 例如：

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   若要解决此问题，请添加[/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md)到链接器命令行选项，并确保 uuid.lib 是引用的第一个库。
