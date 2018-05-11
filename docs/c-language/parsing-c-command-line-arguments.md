---
title: 分析 C 命令行参数 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line, parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: ffce8037-2811-45c4-8db4-1ed787859c80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 53b61bae046e73c4e49bbcaeb095b7bf230e95dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/03/2018
---
# <a name="parsing-c-command-line-arguments"></a>分析 C 命令行自变量
**Microsoft 专用**  
  
 在解释操作系统命令行上给出的自变量时，Microsoft C 启动代码使用下列规则：  
  
-   参数用空白分隔，空白可以是一个空格或制表符。  
  
-   无论其中是否包含空白，双引号括起来的字符串均被解释为单个参数。 带引号的字符串可以嵌入在自变量内。 请注意，插入符号 (^) 未被识别为转义符或者分隔符。  
  
-   前面有反斜杠的双引号 \\" 被解释为原义双引号 (")。  
  
-   反斜杠按其原义解释，除非它们紧位于双引号之前。  
  
-   如果偶数个反斜杠后跟双引号，则每对反斜杠 (\\\\) 中有一个反斜杠 (\\) 被置于 `argv` 数组中，而双引号 (") 被解释为字符串分隔符。  
  
-   如果奇数个反斜杠后跟双引号，则每对反斜杠 (\\\\) 中有一个反斜杠 (\\) 被置于 ) is placed in the `argv` 数组中，而通过剩余的反斜杠，双引号被解释为反义序列，从而使原义双引号 (") 放置在 `argv` 中。  
  
 此列表通过显示命令行参数的多个示例的传递到 `argv` 的解释结果来阐释上述规则。 在第二列、第三列和第四列中列出的输出来自于遵循列表的 ARGS.C 程序。  
  
|命令行输入|argv[1]|argv[2]|argv[3]|  
|-------------------------|---------------|---------------|---------------|  
|`"a b c" d e`|`a b c`|`d`|`e`|  
|`"ab\"c" "\\" d`|`ab"c`|`\`|`d`|  
|`a\\\b d"e f"g h`|`a\\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
## <a name="example"></a>示例  
  
### <a name="code"></a>代码  
  
```  
// Parsing_C_Commandline_args.c  
// ARGS.C illustrates the following variables used for accessing  
// command-line arguments and environment variables:  
// argc  argv  envp  
//  
  
#include <stdio.h>  
  
int main( int argc, // Number of strings in array argv  
 char *argv[],      // Array of command-line argument strings  
 char **envp )      // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    printf_s( "\nCommand-line arguments:\n" );  
    for( count = 0; count < argc; count++ )  
        printf_s( "  argv[%d]   %s\n", count, argv[count] );  
  
    // Display each environment variable.  
    printf_s( "\nEnvironment variables:\n" );  
    while( *envp != NULL )  
        printf_s( "  %s\n", *(envp++) );  
  
    return;  
}  
```  
  
## <a name="comments"></a>注释  
 此程序中输出的一个示例是：  
  
```  
Command-line arguments:  
  argv[0]   C:\MSC\TEST.EXE  
  
Environment variables:  
  COMSPEC=C:\NT\SYSTEM32\CMD.EXE  
  
  PATH=c:\nt;c:\binb;c:\binr;c:\nt\system32;c:\word;c:\help;c:\msc;c:\;  
  PROMPT=[$p]   
  TEMP=c:\tmp  
  TMP=c:\tmp  
  EDITORS=c:\binr  
  WINDIR=c:\nt        
```  
  
 **结束 Microsoft 专用**  
  
## <a name="see-also"></a>请参阅  
 [main 函数和程序执行](../c-language/main-function-and-program-execution.md)
