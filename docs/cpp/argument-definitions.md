---
title: 自变量定义
ms.date: 11/04/2016
helpviewer_keywords:
- envp argument
- main function, arguments
- arguments [C++], for main function
- argv argument
- argc argument
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
ms.openlocfilehash: 3f194f337288f86190177fc7fa0f63bf18f45665
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50444182"
---
# <a name="argument-definitions"></a>自变量定义

原型中的自变量

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

允许通过命令行分析参数并（可选）允许访问环境变量。 自变量定义如下所示：

*argc*<br/>
一个整数，包含后面的自变量计数*argv*。 *Argc*参数始终是大于或等于 1。

*argv*<br/>
表示由杂注用户输入的命令行自变量的以 null 结尾的字符串的数组。 按照约定， `argv` **[0]** 是与调用程序，该命令`argv` **[1]** 是第一个命令行参数，依此类推，直到`argv` **[**`argc`**]**，项始终为 NULL。 请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)有关取消命令行处理的信息。

第一个命令行参数始终是`argv` **[1]** 和最后一项`argv` **[** `argc` -1 **]**。

> [!NOTE]
>  按照约定，`argv`[0] 是用于调用程序的命令。  但是，就可以生成进程使用[CreateProcess](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)并且使用第一个和第二个参数 (*lpApplicationName*并*lpCommandLine*)， `argv`**[0]** 可能不是可执行名称; 而使用[GetModuleFileName](/windows/desktop/api/libloaderapi/nf-libloaderapi-getmodulefilenamea)来检索可执行文件的名称和其完全限定的路径。

## <a name="microsoft-specific"></a>Microsoft 专用

*envp*<br/>
*Envp*数组，它是在许多 UNIX 系统中的一个常见扩展，在 Microsoft c + + 中使用。 它是表示用户环境中的变量集的字符串的数组。 该数组由 NULL 项终止。 它可以声明为指向的指针的数组**char (char** \*envp []**)** 或作为指针到指向**char (char** \* \*envp **)**。 如果程序使用`wmain`而不是`main`，使用`wchar_t`数据类型而非**char**。 环境块传递给`main`和`wmain`是当前环境的"冻结"副本。 如果随后更改通过调用环境`putenv`或`_wputenv`，在当前环境 (由返回`getenv` / `_wgetenv`并`_environ` /  `_wenviron`变量) 将将不会发生更改，但由 envp 指向的块。 请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)有关取消环境处理的信息。 此自变量在 C 中是 ANSI 兼容的，但在 C++ 中不是这样。

**结束 Microsoft 专用**

## <a name="example"></a>示例

下面的示例演示如何使用*argc*， *argv*，并*envp*参数`main`:

```cpp
// argument_definitions.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>

using namespace std;
int main( int argc, char *argv[], char *envp[] ) {
    int iNumberLines = 0;    // Default is no line numbers.

    // If /n is passed to the .exe, display numbered listing
    // of environment variables.

    if ( (argc == 2) && _stricmp( argv[1], "/n" ) == 0 )
         iNumberLines = 1;

    // Walk through list of strings until a NULL is encountered.
    for( int i = 0; envp[i] != NULL; ++i ) {
        if( iNumberLines )
            cout << i << ": " << envp[i] << "\n";
    }
}
```

## <a name="see-also"></a>请参阅

[main：程序启动](../cpp/main-program-startup.md)