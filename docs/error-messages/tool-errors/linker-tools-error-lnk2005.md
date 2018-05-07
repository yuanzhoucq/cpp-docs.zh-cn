---
title: 链接器工具错误 LNK2005 |Microsoft 文档
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
ms.openlocfilehash: f853bec220c7d46ed2a0c44ac1e1d45fbca8318f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-error-lnk2005"></a>链接器工具错误 LNK2005
*符号*对象中已定义  
  
符号*符号*已定义多次。   
  
此错误后跟错误[LNK1169](../../error-messages/tool-errors/linker-tools-error-lnk1169.md)。  
  
### <a name="possible-causes-and-solutions"></a>可能的原因和解决方案  
  
通常，此错误意味着破坏了你*单一定义规则*，这允许你跨的整个可执行文件只有一个定义任何使用的模板、 函数、 类型或对象在给定的对象文件中，而且只有一个定义外部可见的对象或函数。  
  
下面是此错误的一些常见原因。  
  
-   当标头文件定义一个变量时，可能出现此错误。 例如，如果在你项目中，在多个源文件中包含此标头文件，则会出现错误：  
  
    ```h  
    // LNK2005_global.h  
    int global_int;  // LNK2005
    ```  
  
    可能的解决方案包括：  
  
    -   声明变量`extern`标头文件中： `extern int global_int;`，然后定义并根据需要将其初始化且只有一个源文件中： `int global_int = 17;`。 此变量现在是全局，你可以使用任何源文件中通过声明它`extern`，例如，通过包含标头文件。 我们建议变量必须是全局的此解决方案，但良好的软件工程做法最大程度减少全局变量。  
    
    -   声明变量[静态](../../cpp/storage-classes-cpp.md#static): `static int static_int = 17;`。 这会限制到当前的对象文件中，定义的作用域，并允许多个对象文件具有其自己的变量的副本。 我们不建议你在由于可能出现的与全局变量的混淆情况下将在标头文件中定义静态变量。 更愿意将静态变量的定义移到使用它们的源文件。  
  
    -   声明变量[selectany](../../cpp/selectany.md): `__declspec(selectany) int global_int = 17;`。 这将告知链接器来选取一个定义，以便使用由所有外部引用，并丢弃其余。 合并导入库时，此解决方案是有时很有用。 否则，我们不建议这样做作为一种方法，以避免链接器错误。  
  
-   标头文件定义不是一个函数时，会出现此错误`inline`。 如果在多个源文件中包括此标头文件，你可执行文件中获取多个定义的函数。  
    
    ```h  
    // LNK2005_func.h  
    int sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    可能的解决方案包括：  
  
    -   添加`inline`关键字对函数： 

        ```h  
        // LNK2005_func_inline.h  
        inline int sample_function(int k) { return 42 * (k % 167); }  
        ```  
  
    -   从标头文件中删除函数体并保留只有声明，然后在一个且仅有一个源文件中实现函数：  
  
        ```h  
        // LNK2005_func_decl.h  
        int sample_function(int);  
        ```  
  
        ```cpp  
        // LNK2005_func_impl.cpp  
        int sample_function(int k) { return 42 * (k % 167); }  
        ```  
-   如果在标头文件中定义类声明的外部的成员函数，也可能发生此错误：  
  
    ```h  
    // LNK2005_member_outside.h  
    class Sample {
    public:
        int sample_function(int);  
    };
    int Sample::sample_function(int k) { return 42 * (k % 167); }  // LNK2005
    ```  
  
    若要解决此问题，将在类中的成员函数定义。 类声明中定义的成员函数进行了隐式内联。  
  
    ```h  
    // LNK2005_member_inline.h  
    class Sample {
    public:
        int sample_function(int k) { return 42 * (k % 167); }  
    };
    ```  
  
-   如果将链接到多个版本的标准库或 CRT，则可能出现此错误。 例如，如果你尝试将同时零售和调试 CRT 库或库中的静态和动态版本或两个不同版本的标准库链接到可执行文件，则此错误，可能被报告多次。 若要解决此问题，请从链接命令中删除每个库的所有只保留一个的副本。 我们不建议您混用零售和调试库或不同版本的库，在同一可执行文件。  
  
    若要告知链接器命令行上使用库之外的默认值，指定要使用，并且使用的库[/NODEFAULTLIB](../../build/reference/nodefaultlib-ignore-libraries.md)选项以禁用默认库。 在 IDE 中，添加到项目中以指定要使用，，然后打开的库的引用**属性页**对话框为你的项目，并在**链接器**，**输入**属性页上，设置**忽略所有默认库**，或**忽略特定默认库**属性禁用默认库。   
  
-   如果当你使用混合使用静态和动态库，会出现此错误[/clr](../../build/reference/clr-common-language-runtime-compilation.md)选项。 例如，如果使用的 DLL 中生成可执行文件中的静态 CRT 的该链接可以出现此错误。 若要解决此问题，请使用仅静态库或仅动态库整个可执行文件和生成要在可执行文件中使用任何库。  
  
-   如果符号封装的函数，则会出现此错误 (由使用编译[/Gy](../../build/reference/gy-enable-function-level-linking.md)) 和它包含在多个文件，但在各编译间已改变。 若要解决此问题，请重新编译包含打包的函数的所有文件。  
  
-   如果在不同库中的两个成员对象中以不同方式定义该符号，使用这两个成员对象，则会出现此错误。 若要解决此问题，静态链接库时的一种方法是从仅一个库中，使用成员对象并将该库第一次包含在链接器命令行。 若要使用这两个符号，必须创建一种方法将它们区分开来。 例如，如果可以生成来自源的库，你可以包装每个唯一的命名空间中的库。 或者，你可以创建一个新的包装库，使用唯一名称来包装对其中一个原始库的引用，将新的库链接到原始的库，然后链接到新库而不是原始库的可执行文件。  
  
-   如果可能发生此错误`extern const`变量被定义两次，并在每个定义中具有不同的值。 若要解决此问题，定义常量的一次，或者使用命名空间或`enum class`来区分常量的定义。  
  
-   Uuid.lib 结合使用与定义 Guid （例如 oledb.lib 和 adsiid.lib） 的其他.lib 文件，可能出现此错误。 例如：  
  
    ```Output  
    oledb.lib(oledb_i.obj) : error LNK2005: _IID_ITransactionObject  
    already defined in uuid.lib(go7.obj)  
    ```  
  
     若要解决此问题，将添加[/FORCE:MULTIPLE](../../build/reference/force-force-file-output.md)到链接器命令行选项，并确保 uuid.lib 是引用的第一个库。
  
## <a name="additional-information"></a>其他信息  
  
如果你使用的较旧版本的工具集，请参阅有关此错误的特定原因的详细信息这些知识库文章：  
  
-   [出现 LNK2005 错误，则当以错误的顺序在 Visual c + + 链接的 CRT 库和 MFC 库](https://support.microsoft.com/kb/148652)  
  
-   [修复： 全局重载的删除运算符导致 LNK2005](https://support.microsoft.com/kb/140440)  
  
-   [在编译 Visual c + + ATL 可执行文件 (.exe) 项目时收到 LNK2005 错误](https://support.microsoft.com/kb/184235)。  
  
