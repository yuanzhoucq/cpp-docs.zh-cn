---
title: 链接器工具错误 LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 6090478c3761c477250b6706a350e261b51f2a05
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353242"
---
# <a name="linker-tools-error-lnk2005"></a>链接器工具错误 LNK2005

> *已在*对象中定义的符号

符号*已*多次定义。

此错误后跟致命错误[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。

### <a name="possible-causes-and-solutions"></a>可能的原因和解决方案

通常，此错误意味着您已损坏*一个定义规则*，该定义规则只允许给定对象文件中任何已使用的模板、函数、类型或对象定义一个定义，并且在整个可执行文件中仅允许一个外部可见对象或函数的定义。

以下是此错误的一些常见原因。

- 当标头文件定义变量时，可能会发生此错误。 例如，如果将此标头文件包含在项目中的多个源文件中，则会导致错误：

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   可能的解决方案包括：

  - 声明标头文件中`extern`的变量： `extern int global_int;`，然后定义它，并选择性地在一个和只有一个源文件中初始化`int global_int = 17;`它： 。 此变量现在是一个全局变量，您可以通过声明它`extern`（例如，包括标头文件）在任何源文件中使用。 对于必须是全局的变量，我们建议使用此解决方案，但良好的软件工程实践可最大限度地减少全局变量。

  - 声明变量[静态](../../cpp/storage-classes-cpp.md#static)： `static int static_int = 17;`。 这将定义的范围限制为当前对象文件，并允许多个对象文件具有自己的变量副本。 我们不建议您在头文件中定义静态变量，因为可能会与全局变量混淆。 更喜欢将静态变量定义移动到使用它们的源文件中。

  - 声明变量[selectany](../../cpp/selectany.md) `__declspec(selectany) int global_int = 17;`： . . 这告诉链接器选择一个定义供所有外部引用使用，并丢弃其余。 此解决方案有时在组合导入库时很有用。 否则，我们不推荐它作为避免链接器错误的一种方式。

- 当标头文件定义不是`inline`的函数时，可能会发生此错误。 如果在此头文件包含多个源文件中，则可以在可执行文件中获取该函数的多个定义。

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   可能的解决方案包括：

  - 将`inline`关键字添加到函数：

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - 从头文件中删除函数正文，只保留声明，然后在一个和只有一个源文件中实现该函数：

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- 如果在标头文件中的类声明之外定义成员函数，也可能发生此错误：

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   要解决此问题，在类中移动成员函数定义。 在类声明中定义的成员函数隐式内联。

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- 如果链接了多个版本的标准库或 CRT，则可能发生此错误。 例如，如果您尝试将零售库和调试 CRT 库或库的静态和动态版本或标准库的两个不同版本链接到可执行文件，则此错误可能会报告多次。 要解决此问题，请从链接命令中删除每个库除一个副本外的所有副本。 我们不建议您将零售库和调试库或库的不同版本混合在同一可执行文件中。

   要告诉链接器在命令行上使用默认值以外的库，请指定要使用的库，并使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)选项禁用默认库。 在 IDE 中，添加对项目的引用以指定要使用的库，然后打开项目**的属性页**对话框，并在 **"链接器**、**输入**属性"页中设置 **"忽略所有默认库**"或 **"忽略特定默认库"** 属性以禁用默认库。

- 如果在使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项时混合使用静态和动态库，则可能发生此错误。 例如，如果构建一个 DLL 以用于静态 CRT 中的链接的可执行文件，则可能发生此错误。 要解决此问题，请使用静态库或仅对整个可执行文件以及生成要在可执行文件中使用的任何库使用动态库。

- 如果符号是打包函数（通过编译[创建）并且](../../build/reference/gy-enable-function-level-linking.md)它包含在多个文件中，但在编译之间更改，则可能发生此错误。 要解决此问题，请重新编译包含打包函数的所有文件。

- 如果符号在不同的库中的两个成员对象中定义不同，并且使用两个成员对象，则可能发生此错误。 当库以静态链接时解决此问题的一种方法是仅从一个库中使用成员对象，并首先在链接器命令行中包括该库。 要使用这两个符号，必须创建一种方法来区分它们。 例如，如果可以从源生成库，则可以将每个库包装在一个唯一的命名空间中。 或者，您可以创建一个新的包装库，该库使用唯一名称来包装对其中一个原始库的引用，将新库链接到原始库，然后将可执行文件链接到新库而不是原始库。

- 如果`extern const`变量定义两次，并且每个定义中具有不同的值，则可能发生此错误。 要解决此问题，请仅定义一次常量，或使用命名空间或`enum class`定义来区分常量。

- 如果将 uuid.lib 与其他定义 GUID 的文件（例如 oledb.lib 和 adiid.lib）结合使用，则可能发生此错误。 例如：

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   要解决此问题，请确保将[/FORCE：MULTI](../../build/reference/force-force-file-output.md)添加到链接器命令行选项，并确保 uuid.lib 是第一个引用的库。
