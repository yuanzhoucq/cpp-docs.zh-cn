---
title: 链接器工具错误 LNK2005
ms.date: 11/04/2016
f1_keywords:
- LNK2005
helpviewer_keywords:
- LNK2005
ms.assetid: d9587adc-68be-425c-8a30-15dbc86717a4
ms.openlocfilehash: 278f05b8338ac4238d6862fd7b9bd7744f6c8ee5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225210"
---
# <a name="linker-tools-error-lnk2005"></a>链接器工具错误 LNK2005

> 已在对象中定义的*符号*

符号*符号*被定义了多次。

此错误后跟错误[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。

### <a name="possible-causes-and-solutions"></a>可能的原因和解决方法

通常情况下，此错误表示您已经损坏了*一个定义规则*，该规则只允许在给定对象文件中对任何已使用的模板、函数、类型或对象进行一种定义，对外部可见对象或函数的整个可执行文件只能有一个定义。

下面是导致此错误的一些常见原因。

- 当标头文件定义变量时，会出现此错误。 例如，如果在项目的多个源文件中包含此标头文件，则会出现错误：

    ```h
    // LNK2005_global.h
    int global_int;  // LNK2005
    ```

   可能的解决方案包括：

  - 在 **`extern`** 头文件中声明变量： `extern int global_int;` ，然后定义该变量，并根据需要将其初始化为一个且仅有一个源文件： `int global_int = 17;` 。 此变量现在是全局的，可以通过声明（ **`extern`** 例如，通过包含头文件）在任何源文件中使用。 对于必须是全局变量的变量，建议采用此解决方案，但优秀的软件工程实践会将全局变量降到最低。

  - 将变量声明为[static](../../cpp/storage-classes-cpp.md#static)： `static int static_int = 17;` 。 这会将定义的范围限制为当前对象文件，并允许多个对象文件具有其自己的变量副本。 不建议在头文件中定义静态变量，因为可能会与全局变量混淆。 更愿意将静态变量定义移到使用它们的源文件中。

  - 声明变量[selectany](../../cpp/selectany.md)： `__declspec(selectany) int global_int = 17;` 。 这会通知链接器选择一个定义供所有外部引用使用，并放弃其余的定义。 在组合导入库时，此解决方案有时很有用。 否则，不建议使用它作为避免链接器错误的方法。

- 当标头文件定义的函数不是时，会发生此错误 **`inline`** 。 如果将此头文件包含在多个源文件中，则会在可执行文件中获取函数的多个定义。

    ```h
    // LNK2005_func.h
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   可能的解决方案包括：

  - 将 **`inline`** 关键字添加到函数：

    ```h
    // LNK2005_func_inline.h
    inline int sample_function(int k) { return 42 * (k % 167); }
    ```

  - 删除标头文件中的函数体并仅保留声明，然后在一个且仅一个源文件中实现函数：

    ```h
    // LNK2005_func_decl.h
    int sample_function(int);
    ```

    ```cpp
    // LNK2005_func_impl.cpp
    int sample_function(int k) { return 42 * (k % 167); }
    ```

- 如果在标头文件中的类声明外部定义成员函数，也可能发生此错误：

    ```h
    // LNK2005_member_outside.h
    class Sample {
    public:
        int sample_function(int);
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```

   若要解决此问题，请将成员函数定义移动到类中。 类声明内定义的成员函数是隐式内联的。

    ```h
    // LNK2005_member_inline.h
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }
    };
    ```

- 如果链接了多个版本的标准库或 CRT，则会发生此错误。 例如，如果你尝试同时链接零售和调试 CRT 库，或同时链接库的静态和动态版本，或者将两个不同版本的标准库链接到可执行文件，则可能会多次报告此错误。 若要解决此问题，请从 link 命令中删除每个库的所有副本，而不是每个副本。 建议你不要在同一可执行文件中混合使用零售版和调试库或不同版本的库。

   若要通知链接器使用默认值而不是默认值，请在命令行上指定要使用的库，并使用[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)选项禁用默认库。 在 IDE 中，添加对项目的引用以指定要使用的库，然后打开项目的 "**属性页**" 对话框，在 "**链接器**"、"**输入**" 属性页中，设置 "**忽略所有默认库**" 或 "**忽略特定默认**库属性" 以禁用默认库。

- 如果在使用[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项时混合使用了静态和动态库，则会发生此错误。 例如，如果在可执行文件中使用静态 CRT 链接，则会出现此错误。 若要解决此问题，请仅使用静态库或仅为整个可执行文件和生成的要在可执行文件中使用的任何库使用动态库。

- 如果符号为打包的函数（通过用[/gy](../../build/reference/gy-enable-function-level-linking.md)编译创建），并且它包含在多个文件中，但在编译之间发生了更改，则会出现此错误。 若要解决此问题，请重新编译包含打包函数的所有文件。

- 如果在不同库中的两个成员对象中以不同方式定义符号，同时使用这两个成员对象，则会发生此错误。 在以静态方式链接库时解决此问题的一种方法是仅使用一个库中的成员对象，并首先在链接器命令行中包含该库。 若要同时使用这两个符号，必须创建一种方法来区分它们。 例如，如果您可以从源生成库，则可以将每个库包装在唯一的命名空间中。 或者，你可以创建一个新的包装库，该库使用唯一名称来包装对某个原始库的引用，将新库链接到原始库，然后将可执行文件链接到新库，而不是原始库。

- 如果 `extern const` 变量被定义了两次，并在每个定义中具有不同的值，则会出现此错误。 若要解决此问题，请仅定义一次常数，或使用命名空间或 **`enum class`** 定义来区分这些常量。

- 如果将 uuid 与定义 Guid （例如 oledb .lib 和 adsiid）的其他 .lib 文件结合使用，则会出现此错误。 例如：

    ```Output
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject
    already defined in uuid.lib(go7.obj)
    ```

   若要解决此问题，请将[/force： MULTIPLE](../../build/reference/force-force-file-output.md)添加到链接器命令行选项，并确保 uuid 是引用的第一个库。
