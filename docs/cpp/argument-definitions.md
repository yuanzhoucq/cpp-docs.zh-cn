---
title: "参数定义 | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "argc 参数"
  - "参数 [C++], 对于主函数"
  - "argv 参数"
  - "envp 参数"
  - "主函数, 参数"
ms.assetid: 6148cbf3-ebe8-44f2-b277-de4b723991c7
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 参数定义
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

原型中的参数  
  
```  
  
int main( int argc[ , char *argv[ ] [, char *envp[ ] ] ] ); int wmain( int argc[ , wchar_t *argv[ ] [, wchar_t *envp[ ] ] ] );  
```  
  
 允许通过命令行分析参数并（可选）允许访问环境变量。  参数定义如下所示：  
  
 `argc`  
 包含 `argv` 后面的参数计数的整数。  `argc` 参数始终大于或等于 1。  
  
 `argv`  
 表示由杂注用户输入的命令行参数的以 null 结尾的字符串的数组。  按照约定，`argv`**\[0\]** 是用于调用程序的命令，`argv`**\[1\]** 是第一个命令行参数，依此类推，直到 `argv`**\[\]**`argc`，它始终为 **NULL**。  有关取消命令行处理的信息，请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)。  
  
 第一个命令行参数始终是 `argv`**\[1\]**，且最后一个命令行参数是 `argv`**\[**`argc` – 1**\]**。  
  
> [!NOTE]
>  按照约定，`argv`**\[0\]** 是用于调用程序的命令。但是，可以使用 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms683197) 来生成进程，并且如果您使用第一个参数和第二个参数（`lpApplicationName` 和 `lpCommandLine`），则 `argv`**\[0\]** 可能不是可执行文件的名称；使用 [GetModuleFileName](http://msdn.microsoft.com/library/windows/desktop/ms683197) 检索可执行文件名称及其完全限定路径。  
  
## Microsoft 专用  
 `envp`  
 在 Microsoft C\+\+ 中使用 `envp` 数组（它是许多 UNIX 系统中的常见扩展）。  它是表示用户环境中的变量集的字符串的数组。  该数组由 **NULL** 项终止。  它可以声明为指向 **char \(char** \*envp\[ \]**\)** 的指针的数组或一个指向 **char \(char** \*\*envp**\)** 的指针的指针。  如果程序使用 **wmain** 而不是 **main**，请使用 `wchar_t` 数据类型而不是 `char`。  传递给 **main** 和 **wmain** 的环境块是当前环境的“冻结”副本。  如果您随后通过调用 **putenv** 或 `_wputenv` 更改环境，则当前环境（由 `getenv`\/`_wgetenv` 和 `_environ`\/ `_wenviron` 变量返回）将发生更改，但由 envp 指向的块将不会更改。  有关取消环境处理的信息，请参阅[自定义命令行处理](../cpp/customizing-cpp-command-line-processing.md)。  此参数在 C 中是 ANSI 兼容的，但在 C\+\+ 中不是这样。  
  
## 结束 Microsoft 专用  
  
## 示例  
 下面的示例演示如何将 `argc`、`argv` 和 `envp` 参数用于 **main**：  
  
```  
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
  
## 请参阅  
 [main：程序启动](../cpp/main-program-startup.md)