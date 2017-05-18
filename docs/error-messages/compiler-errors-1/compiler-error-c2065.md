---
title: "编译器错误 C2065 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 5a3a0d4389a958f421f23a4dc96a395eaf3e22ab
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-error-c2065"></a>编译器错误 C2065
“identifier”：未声明的标识符  
  
编译器找不到标识符的声明。 如果标识符是一个变量，你必须在声明中指定变量的类型，然后才能使用。 如果该标识符是函数名称，将必须在声明中指定该函数使用的参数，然后才能使用该函数。 如果该标识符是的标记的用户定义的类型，例如，`class`或`struct`，必须声明该标记的类型，然后才能使用。 如果该标识符是类型别名，必须通过使用声明的类型`using`声明或`typedef`前，可以使用类型。  
  
有许多可能的原因，此错误。 下面是一些最常见的问题︰
  
## <a name="example-misspelled-identifier"></a>示例︰ 拼写错误的标识符  
  
此错误通常在标识符名称拼写错误，或标识符使用错误的大写和小写字母时发生。 声明中的名称必须与你使用的名称完全匹配。  
  
```cpp  
// C2065_spell.cpp  
// compile with: cl /EHsc C2065_spell.cpp 
#include <iostream> 
using namespace std; 
int main() { 
    int someIdentifier = 42; 
    cout << "Some Identifier: " << SomeIdentifier << endl;   
    // C2065: 'SomeIdentifier': undeclared identifier 
    // To fix, correct the spelling:  
    // cout << "Some Identifier: " << someIdentifier << endl;   
}  
```
  
## <a name="example-missing-header-file"></a>示例︰ 缺少标头文件  
  
你没有包括头文件声明标识符。 请确保在使用它的每个源代码文件中包括包含标识符的声明的文件。  
  
```cpp  
// C2065_header.cpp  
// compile with: cl /EHsc C2065_spell.cpp 

//#include <stdio.h> 
int main() { 
    fpos_t file_position = 42; // C2065: 'fpos_t': undeclared identifier 
    // To fix, uncomment the #include <stdio.h> line
    // to include the header where fpos_t is defined  
} 
```  
  
如果你定义，可能会看到此错误在 Windows 桌面应用程序源文件`VC_EXTRALEAN`， `WIN32_LEAN_AND_MEAN`，或`WIN32_EXTRA_LEAN`。 这些预处理器宏排除某些头文件从 windows.h 和 afxv\_w32.h 加快编译。 查看 windows.h 和 afxv_w32.h，了解排除的最新描述。  
  
## <a name="eample-missing-closing-quote"></a>Eample︰ 缺少右引号  
  
如果字符串常量后缺少右引号，则可能出现此错误。 这是一种混淆编译器简便方法。 
  
```cpp  
// C2065_quote.cpp  
// compile with: cl /EHsc C2065_quote.cpp 
#include <iostream>  

int main() { 
    // Fix this issue by adding the closing quote to "Aaaa"
    char * first = "Aaaa, * last = "Zeee"; 
    std::cout << "Name: " << first 
        << " " << last << std::endl; // C2065: 'last': undeclared identifier 
} 
```  
  
## <a name="example-use-iterator-outside-for-loop-scope"></a>示例︰ 使用 for 循环范围之外的迭代器  
  
如果声明中的迭代器变量，会出现此错误`for`循环，然后尝试使用该迭代器变量的作用域之外`for`循环。 编译器启用[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)默认情况下的编译器选项。 请参阅[调试迭代器支持](../../standard-library/debug-iterator-support.md)有关详细信息。  
  
```cpp  
// C2065_iter.cpp  
// compile with: cl /EHsc C2065_iter.cpp 
#include <iostream> 
#include <string> 

int main() {
    // char last = '!'; 
    std::string letters{ "ABCDEFGHIJKLMNOPQRSTUVWXYZ" }; 
    for (const char& c : letters) {
        if ('Q' == c) {
            std::cout << "Found Q!" << std::endl;
        }
        // last = c;
    }
    std::cout << "Last letter was " << c << std::endl; // C2065
    // Fix by using a variable declared in an outer scope.
    // Uncomment the lines that declare and use 'last' for an example.
    // std::cout << "Last letter was " << last << std::endl; // C2065
} 
```  
  
## <a name="example-preprocessor-removed-declaration"></a>预处理器已删除的声明示例︰  
  
如果引用的函数或在未编译为你的当前配置的有条件地编译代码的变量，则可能出现此错误。 如果你在生成环境中当前不支持的标头文件中调用函数，也会发生此问题。 如果定义特定的预处理器宏时，某些变量或函数才可用，，请确保定义相同的预处理器宏时，可以仅编译调用这些函数的代码。 此问题是很容易识别在 IDE 中，因为如果没有为当前生成配置定义所需的预处理器宏，该函数的声明灰显。  
  
这是代码的适用于构建在调试，但不是零售的一个示例︰  
  
```cpp  
// C2065_defined.cpp
// Compile with: cl /EHsc /W4 /MT C2065_defined.cpp
#include <iostream>
#include <crtdbg.h>
#ifdef _DEBUG
    _CrtMemState oldstate;
#endif
int main() {
    _CrtMemDumpStatistics(&oldstate); 
    std::cout << "Total count " << oldstate.lTotalCount; // C2065
    // Fix by guarding references the same way as the declaration:
    // #ifdef _DEBUG
    //    std::cout << "Total count " << oldstate.lTotalCount;
    // #endif
}
```
  
## <a name="example-use-an-unscoped-identifier"></a>示例︰ 使用未区分范围的标识符  
  
如果你的标识符的范围不正确，可能出现此错误。 例如，当 c + + 标准库函数和运算符未完全限定的命名空间，或不使`std`到使用的当前作用域的命名空间`using`指令，编译器找不到它们。 若要解决此问题，你必须完全限定的标识符名称，或指定的命名空间与`using`指令。  
  
此示例无法进行编译因为`cout`和`endl`中定义`std`命名空间︰  
  
```cpp  
// C2065_scope.cpp  
// compile with: cl /EHsc C2065_scope.cpp 
// using namespace std;   // Uncomment this line to fix  
#include <iostream>  
int main() {  
    cout << "Hello" << endl;   // C2065 'cout': undeclared identifier 
                               // C2065 'endl': undeclared identifier
    // Or try the following line instead  
    std::cout << "Hello" << std::endl;  
}
```  
  
内部声明的标识符`class`， `struct`，或`enum class`类型，还必须使用封闭作用域的名称进行限定。
  
## <a name="example-ccli-type-deduction-failure"></a>示例︰ C + + /cli CLI 类型推理失败  
  
如果不能从所使用的参数推导预期的类型参数，会调用泛型函数时，此错误。 有关详细信息，请参阅[泛型函数 (C + + /cli CLI)](../../windows/generic-functions-cpp-cli.md)。  
  
```cpp  
// C2065_b.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
int main() {  
   // global generic function call  
   G<T>(10);   // C2065  
   G<int>(10);   // OK - fix with a specific type argument  
}  
```  
  
## <a name="example-ccli-attribute-parameters"></a>示例︰ C + + /cli CLI 属性参数  
  
此错误还可能来自于为 Visual C++ 2005 执行的编译器一致性工作：Visual C++ 特性的参数检查。  
  
```cpp  
// C2065_attributes.cpp  
// compile with: cl /c /clr C2065_attributes.cpp  
[module(DLL, name=MyLibrary)];   // C2065  
// try the following line instead  
// [module(dll, name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```  

