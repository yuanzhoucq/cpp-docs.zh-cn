---
title: 分析 C++ 命令行自变量
ms.date: 11/04/2016
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
ms.openlocfilehash: 53873fa9340253ab5e8459eb442385641246f930
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50471027"
---
# <a name="parsing-c-command-line-arguments"></a>分析 C++ 命令行自变量

**Microsoft 专用**

在解释操作系统命令行上给定自变量时，Microsoft C/C++ 启动代码将使用以下规则：

- 参数用空白分隔，空白可以是一个空格或制表符。

- 插入符号 (^) 未被识别为转义符或者分隔符。 字符在被传递到前由操作系统中的命令行分析器完全处理`argv`程序中的数组。

- 由双引号括起来的字符串 ("*字符串*") 被解释为单个参数，而不考虑包含空白。 带引号的字符串可以嵌入在自变量内。

- 前面有反斜杠的双引号 (\\") 被解释为原义双引号字符 (")。

- 反斜杠按其原义解释，除非它们紧位于双引号之前。

- 如果偶数个反斜杠后跟双引号，一个反斜杠被置于`argv`数组，每对反斜杠，双引号被解释为字符串分隔符。

- 如果奇数个反斜杠后跟双引号，一个反斜杠被置于`argv`数组中的每对反斜杠和双引号由剩余反斜杠，从而导致原义双引号进行"转义"(")，无法放置在`argv`。

## <a name="example"></a>示例

以下程序演示了如何命令行参数传递：

```cpp
// command_line_arguments.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
int main( int argc,      // Number of strings in array argv
          char *argv[],   // Array of command-line argument strings
          char *envp[] )  // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    cout << "\nCommand-line arguments:\n";
    for( count = 0; count < argc; count++ )
         cout << "  argv[" << count << "]   "
                << argv[count] << "\n";
}
```

下表显示了示例输入和预期的输出，演示上述列表中的规则。

### <a name="results-of-parsing-command-lines"></a>分析命令行的结果

|命令行输入|argv[1]|argv[2]|argv[3]|
|-------------------------|---------------|---------------|---------------|
|`"abc" d e`|`abc`|`d`|`e`|
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|
|`a\\\"b c d`|`a\"b`|`c`|`d`|
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|

**结束 Microsoft 专用**

## <a name="see-also"></a>请参阅

[main：程序启动](../cpp/main-program-startup.md)