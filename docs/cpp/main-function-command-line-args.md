---
title: :::no-loc(main):::函数和命令行参数（c + +）
description: :::no-loc(main):::函数是 c + + 程序的入口点。
ms.date: 01/15/2019
ms.assetid: c6568ee6-40ab-4ae8-aa44-c99e232f64ac
no-loc:
- ':::no-loc(main):::'
- ':::no-loc(wmain):::'
- ':::no-loc(inline):::'
- ':::no-loc(static):::'
- ':::no-loc(_tmain):::'
- ':::no-loc(void):::'
- ':::no-loc(exit):::'
- ':::no-loc(argc):::'
- ':::no-loc(argv):::'
- ':::no-loc(envp):::'
- ':::no-loc(CreateProcess):::'
- ':::no-loc(GetModuleFileName):::'
- ':::no-loc(char):::'
- ':::no-loc(wchar_t):::'
- ':::no-loc(extern):::'
ms.openlocfilehash: 9fe7c7a0808584a70bffa541903866b3de364e5f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87213315"
---
# <a name="no-locmain-function-and-command-line-arguments"></a>:::no-loc(main):::函数和命令行参数

所有 c + + 程序必须具有 `:::no-loc(main):::` 函数。 如果尝试编译不带函数的 c + + *.exe*项目 :::no-loc(main)::: ，编译器将引发错误。 （动态链接库和 :::no-loc(static)::: 库没有 `:::no-loc(main):::` 函数。）`:::no-loc(main):::`函数是源代码开始执行的位置，但在程序进入 `:::no-loc(main):::` 函数之前，所有 :::no-loc(static)::: 没有显式初始值设定项的类成员均设置为零。 在 Microsoft c + + 中，全局 :::no-loc(static)::: 对象还会在进入之前进行初始化 `:::no-loc(main):::` 。 一些限制适用于 `:::no-loc(main):::` 不应用于任何其他 c + + 函数的函数。 `:::no-loc(main):::`函数：

- 无法重载（请参阅[函数重载](function-overloading.md)）。
- 不能声明为 **`:::no-loc(inline):::`** 。
- 不能声明为 **`:::no-loc(static):::`** 。
- 不能提取其地址。
- 无法被调用。

该 :::no-loc(main)::: 函数不具有声明，因为它内置于该语言中。 如果是这样，的声明语法将如下所 `:::no-loc(main):::` 示：

```cpp
int :::no-loc(main):::();
int :::no-loc(main):::(int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[]);
```

**Microsoft 专用**

如果源文件使用 Unicode 宽 :::no-loc(char)::: acters，则可以使用 `:::no-loc(wmain):::` ，这是 :::no-loc(char)::: 的 acter 版本 `:::no-loc(main):::` 。 `:::no-loc(wmain):::` 的声明语法如下所示：

```cpp
int :::no-loc(wmain):::( );
int :::no-loc(wmain):::(int :::no-loc(argc):::, :::no-loc(wchar_t)::: *:::no-loc(argv):::[], :::no-loc(wchar_t)::: *:::no-loc(envp):::[]);
```

你还可以使用 `:::no-loc(_tmain):::` 在 \t\t 中定义的 :::no-loc(char)::: 。 `:::no-loc(_tmain):::`解析为， `:::no-loc(main):::` 除非定义 _UNICODE。 在该示例中，`:::no-loc(_tmain):::` 将解析为 `:::no-loc(wmain):::`。

如果未指定返回值，则编译器提供返回值零。 此外， `:::no-loc(main):::` 和 `:::no-loc(wmain):::` 函数可以声明为返回 **`:::no-loc(void):::`** （没有返回值）。 如果声明 `:::no-loc(main):::` 或 `:::no-loc(wmain):::` 返回 **`:::no-loc(void):::`** ，则不能 :::no-loc(exit)::: 使用[return](../cpp/return-statement-in-program-termination-cpp.md)语句将代码返回到父进程或操作系统。 若要 :::no-loc(exit)::: 在 `:::no-loc(main):::` 或声明为时返回代码 `:::no-loc(wmain):::` **`:::no-loc(void):::`** ，则必须使用 [:::no-loc(exit):::](../cpp/:::no-loc(exit):::-function.md) 函数。

**结束 Microsoft 专用**

## <a name="command-line-arguments"></a>命令行参数

或的参数 `:::no-loc(main):::` `:::no-loc(wmain):::` 允许自变量的命令行分析，还可以选择访问环境变量。 `:::no-loc(argc):::` 和 `:::no-loc(argv):::` 的类型由语言定义。 名称 `:::no-loc(argc):::` 、 `:::no-loc(argv):::` 和 `:::no-loc(envp):::` 是传统的，但你可以将其命名为你喜欢的任何名称。

```cpp
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char):::* :::no-loc(argv):::[], :::no-loc(char):::* :::no-loc(envp):::[]);
int :::no-loc(wmain):::( int :::no-loc(argc):::, :::no-loc(wchar_t):::* :::no-loc(argv):::[], :::no-loc(wchar_t):::* :::no-loc(envp):::[]);
```

自变量定义如下所示：

*:::no-loc(argc):::*<br/>
一个整数，其中包含后面的参数的计数 *:::no-loc(argv):::* 。 *:::no-loc(argc):::* 参数始终大于或等于1。

*:::no-loc(argv):::*<br/>
表示由杂注用户输入的命令行自变量的以 null 结尾的字符串的数组。 按照约定， `:::no-loc(argv):::[0]` 是用于调用程序的命令， `:::no-loc(argv):::[1]` 是第一个命令行参数，依此类推，直到 `:::no-loc(argv):::[:::no-loc(argc):::]` ，这始终为 NULL。 有关抑制命令行处理的信息，请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)。

第一个命令行参数始终是 `:::no-loc(argv):::[1]`，而最后一个命令行参数是 `:::no-loc(argv):::[:::no-loc(argc)::: - 1]`。

> [!NOTE]
> 按照约定， `:::no-loc(argv):::[0]` 是用于调用程序的命令。 但是，可以使用来生成进程， [:::no-loc(CreateProcess):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 并且如果同时使用第一个和第二个参数（*LpApplicationName*和*lpCommandLine*）， `:::no-loc(argv):::[0]` 可能不是可执行文件名称; 请使用 [:::no-loc(GetModuleFileName):::](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew) 检索可执行文件名称及其完全限定路径。

**Microsoft 专用**

*:::no-loc(envp):::*<br/>
*:::no-loc(envp):::* 在 Microsoft c + + 中使用数组，这是许多 UNIX 系统中的通用扩展。 它是表示用户环境中的变量集的字符串的数组。 该数组由 NULL 项终止。 它可以声明为指向（）的指针数组，或者声明为指向（）的指针的 **`:::no-loc(char):::`** `:::no-loc(char)::: *:::no-loc(envp):::[]` 指针 **`:::no-loc(char):::`** `:::no-loc(char)::: **:::no-loc(envp):::` 。 如果程序使用 `:::no-loc(wmain):::` 而不是 `:::no-loc(main):::` ，请使用 **`:::no-loc(wchar_t):::`** 数据类型而不是 **`:::no-loc(char):::`** 。 环境块传递到 `:::no-loc(main):::` ，并 `:::no-loc(wmain):::` 是当前环境的 "冻结" 副本。 如果您随后通过调用或更改环境 `putenv` `_wputenv` ，则当前环境（由 `getenv` 或 `_wgetenv` 和 `_environ` 或 `_wenviron` 变量返回）将发生更改，但指向的块 :::no-loc(envp)::: 将不会更改。 有关取消环境处理的信息，请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)。 此参数在 C 中是 ANSI 兼容的，但在 C++ 中不是这样。

**结束 Microsoft 专用**

### <a name="example"></a>示例

下面的示例演示如何使用 *:::no-loc(argc):::* 、 *:::no-loc(argv):::* 和 *:::no-loc(envp):::* 参数 `:::no-loc(main):::` 执行以下操作：

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::, :::no-loc(char)::: *:::no-loc(argv):::[], :::no-loc(char)::: *:::no-loc(envp):::[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (:::no-loc(argc)::: == 2) && _stricmp( :::no-loc(argv):::[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; :::no-loc(envp):::[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << :::no-loc(envp):::[i] << "\n";
    }
}
```

## <a name="parsing-c-command-line-arguments"></a>分析 c + + 命令行参数

**Microsoft 专用**

在解释操作系统命令行上给出的参数时，Microsoft C/c + + 启动代码使用以下规则：

- 参数用空白分隔，空白可以是一个空格或制表符。

- 脱字号 :::no-loc(char)::: acter （^）未被识别为转义 :::no-loc(char)::: acter 或分隔符。 在将 :::no-loc(char)::: acter 传递到程序中的数组之前，将由操作系统中的命令行分析器完全处理 `:::no-loc(argv):::` 。

- 无论中包含哪些空白，用双引号（"*string*"）括起来的字符串均被解释为单个参数。 带引号的字符串可以嵌入在自变量内。

- 前面带有反斜杠（"）的双引号 \\ 被解释为文字的双引号 :::no-loc(char)::: acter （"）。

- 反斜杠按其原义解释，除非它们紧位于双引号之前。

- 如果偶数个反斜杠后跟双引号，则每对反斜杠中有一个反斜杠被置于数组中， `:::no-loc(argv):::` 而双引号被解释为字符串分隔符。

- 如果奇数个反斜杠后跟双引号，则每对反斜杠中有一个反斜杠被置于数组中， `:::no-loc(argv):::` 而双引号由重反斜杠 "转义" :::no-loc(main)::: ，导致原义双引号（"）放置在中 `:::no-loc(argv):::` 。

### <a name="example"></a>示例

以下程序演示如何传递命令行参数：

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int :::no-loc(main):::( int :::no-loc(argc):::,      // Number of strings in array :::no-loc(argv):::
          :::no-loc(char)::: *:::no-loc(argv):::[],   // Array of command-line argument strings
          :::no-loc(char)::: *:::no-loc(envp):::[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < :::no-loc(argc):::; count++ )
         cout << "  :::no-loc(argv):::[" << count << "]   "
                << :::no-loc(argv):::[count] << "\n";
}
```

下表显示了示例输入和预期输出，并演示了上述列表中的规则。

### <a name="results-of-parsing-command-lines"></a>分析命令行的结果

|命令行输入|:::no-loc(argv):::[1]|:::no-loc(argv):::[2]|:::no-loc(argv):::三维空间|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**结束 Microsoft 专用**

## <a name="wildcard-expansion"></a>通配符扩展

**Microsoft 专用**

可以使用通配符（问号 (?) 和星号 (*)）在命令行上指定文件名和路径参数。

命令行参数由名为 `_set:::no-loc(argv):::` （或 `_wset:::no-loc(argv):::` 在 acter 环境中）的例程处理 :::no-loc(char)::: ，默认情况下，它不会将通配符扩展到字符串数组中的各个字符串 `:::no-loc(argv):::` 。 有关启用通配符扩展的详细信息，请参阅[扩展通配符参数](../c-language/expanding-wildcard-arguments.md)。

**结束 Microsoft 专用**

## <a name="customizing-c-command-line-processing"></a>自定义 C++ 命令行处理

**Microsoft 专用**

如果程序不采用命令行自变量，则可以通过取消使用执行命令行处理的库例程来节省少量空间。 此例程被称为 `_set:::no-loc(argv):::` ，并在[通配符扩展](../cpp/wildcard-expansion.md)中进行了介绍。 若要禁止使用，请在包含函数的文件中定义不执行任何操作的例程 `:::no-loc(main):::` ，并将其命名为 `_set:::no-loc(argv):::` 。 然后，对的定义满足对的调用 `_set:::no-loc(argv):::` `_set:::no-loc(argv):::` ，并且不加载库版本。

同样，如果您从不通过参数访问环境表 `:::no-loc(envp):::` ，则可以提供自己的空例程用于替代 `_set:::no-loc(envp):::` 环境处理例程。 与 `_set:::no-loc(argv):::` 函数一样， `_set:::no-loc(envp):::` 必须将声明为** :::no-loc(extern)::: "C"**。

程序可能会调用 `spawn` `exec` C 运行库中的或系列的例程。 如果是这样，则不应取消环境处理例程，因为使用此例程将环境从父进程传递到子进程。

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[基本概念](../cpp/basic-concepts-cpp.md)
