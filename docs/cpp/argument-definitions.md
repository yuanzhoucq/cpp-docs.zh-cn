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
ms.openlocfilehash: aebd4800ad8d653d532708784ef0a5333211d46b
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857653"
---
# <a name="argument-definitions"></a>自变量定义

原型中的自变量

```cpp
int main( int argc, char* argv[], char* envp[]);
int wmain( int argc, wchar_t* argv[], wchar_t* envp[]);
```

允许通过命令行分析参数并（可选）允许访问环境变量。 自变量定义如下所示：

*argc*<br/>
一个整数，其中包含*argv*中后面的参数的计数。 *Argc*参数始终大于或等于1。

*argv*<br/>
表示由杂注用户输入的命令行自变量的以 null 结尾的字符串的数组。 按照约定，`argv[0]` 是用于调用程序的命令，`argv[1]` 是第一个命令行参数，依此类推，直到 `argv[argc]`，这始终为 NULL。 有关抑制命令行处理的信息，请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)。

第一个命令行参数始终是 `argv[1]`，而最后一个命令行参数是 `argv[argc - 1]`。

> [!NOTE]
> 按照约定，`argv[0]` 是用于调用程序的命令。  但是，可以使用[CreateProcess](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)生成进程，并且如果同时使用第一个和第二个参数（*lpApplicationName*和*lpCommandLine*），`argv[0]` 可能不是可执行文件名称;使用[GetModuleFileName](/windows/win32/api/libloaderapi/nf-libloaderapi-getmodulefilenamew)检索可执行文件名称及其完全限定路径。

**Microsoft 专用**

*envp*<br/>
Microsoft C++中使用的 ENVP 阵列是许多 UNIX 系统中的通用扩展。 它是表示用户环境中的变量集的字符串的数组。 该数组由 NULL 项终止。 它可以声明为指向**char** （`char *envp[]`）或指向**char** （`char **envp`）的指针的指针的数组。 如果程序使用 `wmain` 而不是 `main`，请使用**wchar_t**数据类型，而不是**字符**。 环境块传递到 `main`，`wmain` 是当前环境的 "冻结" 副本。 如果随后通过调用 `putenv` 或 `_wputenv`来更改环境，则当前环境（由 `getenv` 或 `_wgetenv` 和 `_environ` 或 `_wenviron` 变量返回）将发生更改，但 envp 指向的块将不会更改。 有关取消环境处理的信息，请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)。 此参数在 C 中是 ANSI 兼容的，但在 C++ 中不是这样。

**结束 Microsoft 专用**

## <a name="example"></a>示例

下面的示例演示如何使用*argc*、 *argv*和*envp*参数 `main`：

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

## <a name="see-also"></a>另请参阅

[main：程序启动](../cpp/main-program-startup.md)