---
title: "链接器工具错误 LNK2019 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK2019
dev_langs:
- C++
helpviewer_keywords:
- nochkclr.obj
- LNK2019
- _check_commonlanguageruntime_version
ms.assetid: 4392be92-195c-4eb2-bd4d-49cfac3ca291
caps.latest.revision: 39
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 6cad5222fb0d97594d5b13b5cf8903eb2934ee88
ms.openlocfilehash: 86b43f2688b6e1dbfb39dfec681ca9adafd2c093
ms.lasthandoff: 02/24/2017

---
# <a name="linker-tools-error-lnk2019"></a>链接器工具错误 LNK2019
函数“function”中引用了未解析的外部符号“symbol”  
  
 链接器无法找到函数“`symbol`”中使用的外部符号“`function`”的定义。  
  
 有许多问题可能会导致此错误。 本主题将帮助你确定原因并找到解决方案。  
  
 一个*符号*编译器使用函数或全局变量的名称。 *的外部符号*是用来在不同的源或对象文件中定义的符号引用的名称。 链接器必须*解决*，或为每个函数或全局变量由每个已编译的文件，在将其链接到应用程序或 DLL 中找到外部符号的定义。 如果链接器无法在任何链接的文件中找到外部符号的匹配定义，那么它会生成 LNK2019。  
  
 如果生成中未包括拥有符号定义的对象或库文件，可以出现此错误。 如果链接器搜索的符号名称与库或对象文件中定义该符号的名称不匹配，也会出现此问题。 如果调用代码中的名称拼写错误、 使用不同的大小写、 使用不同的调用约定，或指定不同的参数，也可能发生。  
  
 使用 c + + 链接的代码使用[名称修饰](../../error-messages/tool-errors/name-decoration.md)，也称为*名称重整*、 来编码关于变量或函数的类型和调用约定中的符号名称的额外信息。 *修饰名称* 是指链接器搜索用于解析外部符号的名称。 由于类型信息成为了符号修饰名称的一部分，如果使用它的外部符号的声明与其中定义的符号的声明不匹配可能会导致 LNK2019。 为了帮助你找到错误的原因，错误消息会显示这两个"友好名称，"在源代码中，和无法解析的外部符号的修饰的名称 （在括号内） 中使用的名称。 您不必知道如何翻译的修饰的名称，以便能够将其与其他修饰名称进行比较。  
  
 **常见的问题**  
  
 以下是一些导致 LNK2019 的常见问题：  
  
-   **未链接的对象文件或包含符号定义的库。** 在 Visual Studio 中，验证包含定义源代码文件是生成，分别链接为项目的一部分。 在命令行中，验证编译时包含定义的源文件，并且所生成对象文件包含在要链接的文件列表。  
  
-   **符号的声明不拼写与符号的定义相同。** 验证在声明和定义，使用正确的拼写和大小写，并且是使用或调用该符号的任何位置。  
  
-   **使用一个函数，但数量的参数的类型与函数定义不匹配。** 函数声明必须匹配定义。 验证函数调用是否匹配声明以及声明是否匹配定义。 调用模板函数的代码还必须拥有包括与定义相同的模板参数的匹配模板函数声明。 模板声明不匹配的示例，请参阅示例 LNK2019e.cpp 示例部分中。  
  
-   **声明但未定义的函数或变量。** 这通常意味着在标头文件中，存在声明，但不匹配定义实现。 对于成员函数或静态数据成员，实现必须包括类范围选择器。 有关示例，请参阅[缺少函数体或变量](../../error-messages/tool-errors/missing-function-body-or-variable.md)。  
  
-   **调用约定是函数声明和函数定义之间的差异。** 调用约定 ([__cdecl](../../cpp/cdecl.md)， [__stdcall](../../cpp/stdcall.md)， [__fastcall](../../cpp/fastcall.md)，或[__vectorcall](../../cpp/vectorcall.md)) 作为修饰名称的一部分进行编码。 验证调用约定是否相同。  
  
-   **符号定义在 C 文件中，但未使用 extern"C"在 c + + 文件中进行声明。** 作为 C 编译的文件中定义的符号拥有与声明在 c + + 文件中，除非您使用的符号不同的修饰的名称[extern"C"](../../cpp/using-extern-to-specify-linkage.md)修饰符。 验证声明是否匹配每个符号的编译链接。  
  
     同样，如果在 C 程序将使用的 C++ 文件中定义符号，请在定义中使用 `extern "C"` 。  
  
-   **一个符号是定义为静态，然后更高版本在文件外部引用。** 在 c + + 与 C 不同，[全局常量](../../error-messages/tool-errors/global-constants-in-cpp.md)具有`static`链接。 若要避开此限制，你可以在头文件中包括 `const` 初始化并将该标头包括在你的 .cpp 文件中，或者你可以让变量成为非常量并使用常量引用来访问它。  
  
-   **未定义一个类的静态成员。** 静态类成员必须拥有唯一的定义，否则它将违反单个定义规则。 无法以内联方式定义的静态类成员必须通过使用其完全限定名称在一个源文件中进行定义。 如果没有进行定义，那么链接器会生成 LNK2019。  
  
-   **生成依赖项仅定义为解决方案中项目依赖项。** 在 [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)] 的早期版本中，此级别的依赖项已经足够。 但是，从 Visual Studio 2010 中，开始[!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]需要[项目到项目引用](/visualstudio/ide/managing-references-in-a-project)。 如果你的项目没有项目到项目引用，那么你可能收到此链接器错误。 添加项目到项目引用以修复此错误。  
  
-   **你通过使用 Windows 应用程序的设置生成了控制台应用程序**。 如果错误消息是类似于**WinMain 函数中引用的无法解析外部符号**`function_name`，通过使用链接**/subsystem: console**而不是**/SUBSYSTEM:WINDOWS**。 有关此设置的详细信息以及有关如何在 Visual Studio 中设置此属性的说明，请参阅[/SUBSYSTEM （指定子系统）](../../build/reference/subsystem-specify-subsystem.md)。  
  
-   **为在不同的源文件中内联的函数使用不同的编译器选项。** 使用 .cpp 文件中定义的内联函数并在不同源文件中混合使用函数内联编译器可能会导致 LNK2019。 有关详细信息，请参阅[函数内联问题](../../error-messages/tool-errors/function-inlining-problems.md)。  
  
-   **在其范围之外使用自动变量。** 自动（函数范围）变量仅可在该函数的范围内使用。 这些变量不可声明为 `extern` ，也不能在其他源文件中使用。 有关示例，请参阅[自动 （函数范围） 变量](../../error-messages/tool-errors/automatic-function-scope-variables.md)。  
  
-   **调用内部函数，或将参数类型传递到目标体系结构不支持的内部函数。** 例如，如果你使用 AVX2 内部函数，但不是指定[/arch: avx2 可以](../../build/reference/arch-x86.md)编译器选项时，编译器将假定该内部函数是外部函数。 编译器不会生成内联指令，相反，它会生成一个对与内部函数同名的外部符号的调用。 当链接器尝试找到此缺失函数的定义时，它会生成 LNK2019。 验证是否只使用了目标体系结构支持的内部函数和类型。  
  
-   **混合的代码不使用本机 wchar_t 的代码。** 在 Visual C++ 2005 中完成的 C++ 语言一致性工作让 `wchar_t` 成为默认本机类型。 必须使用[/Zc:wchar_t-](../../build/reference/zc-wchar-t-wchar-t-is-native-type.md)编译器选项来生成兼容使用 Visual c + + 的早期版本编译的库和对象文件的代码。 如果并非所有文件都已经使用相同的 **/Zc:wchar_t** 设置进行编译，那么类型引用可能不会解析为兼容的类型。 验证所有库和对象文件中的 `wchar_t` 类型是否兼容，方法是更新使用的类型或在编译时使用一致的 **/Zc:wchar_t** 设置。  
  
 有关 LNK2019 的可能原因和解决方案的详细信息，请参阅堆栈溢出问题 [“什么是未定义的引用/未解析的外部符号错误以及如何修复此错误？”](http://stackoverflow.com/q/12573816/2002113)。  
  
 **诊断工具**  
  
 很难判断为什么链接器无法找到特定的符号定义。 问题通常是你没有在生成中包括代码，或生成选项创建了不同的外部符号修饰名称。 有许多工具和选项可以帮助你诊断 LNK2019 错误。  
  
-   [/Verbose](../../build/reference/verbose-print-progress-messages.md)链接器选项可帮助您确定链接器引用了哪些文件。 这可以帮助验证你的生成中是否包括了包含符号定义的文件。  
  
-   [/导出](../../build/reference/dash-exports.md)和[/ 符号](../../build/reference/symbols.md)选项的 DUMPBIN 实用工具可帮助你发现.dll 和对象或库文件中定义了哪些符号。 验证导出的修饰名称是否匹配链接器搜索的修饰名称。  
  
-   UNDNAME 实用工具可以显示修饰名称的等效未修饰外部符号。  
  
 **示例**  
  
 以下是一些导致 LNK2019 错误的代码示例，以及关于如何修复错误的信息。  
  
 **声明但未定义符号**  
  
 以下示例生成 LNK2019，原因是声明了外部符号但未对其进行定义：  
  
```cpp  
// LNK2019.cpp  
// Compile by using: cl /EHsc LNK2019.cpp  
// LNK2019 expected  
extern char B[100];   // B is not available to the linker  
int main() {  
   B[0] = ' ';   // LNK2019  
}  
```  
  
 以下是另一个示例：  
  
```cpp  
// LNK2019c.cpp  
// Compile by using: cl /EHsc LNK2019c.cpp  
// LNK2019 expected  
extern int i;  
extern void g();  
void f() {  
   i++;  
   g();  
}  
int main() {}  
```  
  
 如果 `i` 和 `g` 没有在生成中的任一文件中定义，那么链接器会生成 LNK2019。 你可以通过将包含定义的源代码文件作为编译的一部分包括在其中来修复错误。 或者，你可以将包含定义的 .obj 文件或 .lib 文件传递到链接器。  
  
 **声明但未定义静态数据成员**  
  
 LNK2019 还可能会在声明了静态数据成员但未对其进行定义时发生。 以下示例生成 LNK2019，并演示如何修复此错误。  
  
```cpp  
// LNK2019b.cpp  
// Compile by using: cl /EHsc LNK2019b.cpp  
// LNK2019 expected  
struct C {  
   static int s;  
};  
  
// Uncomment the following line to fix the error.  
// int C::s;  
  
int main() {  
   C c;  
   C::s = 1;  
}  
```  
  
 **声明参数不匹配定义**  
  
 调用模板函数的代码必须拥有匹配的模板函数声明。 声明必须包括与定义相同的模板参数。 以下示例在用户定义的运算符上生成 LNK2019，并演示如何修复此错误。  
  
```cpp  
// LNK2019e.cpp  
// compile by using: cl /EHsc LNK2019e.cpp  
// LNK2019 expected  
#include <iostream>  
using namespace std;  
  
template<class T> class   
Test {  
   // The operator<< declaration does not match the definition below:  
   friend ostream& operator<<(ostream&, Test&);  
   // To fix, replace the line above with the following:  
   // template<typename T> friend ostream& operator<<(ostream&, Test<T>&);  
};  
  
template<typename T>  
ostream& operator<<(ostream& os, Test<T>& tt) {  
   return os;  
}  
  
int main() {  
   Test<int> t;  
   cout << "Test: " << t << endl;   // LNK2019 unresolved external  
}  
```  
  
 **不一致的 wchar_t 类型定义**  
  
 以下示例创建拥有使用 `WCHAR`的导出的 DLL，其解析为 `wchar_t`。  
  
```cpp  
// LNK2019g.cpp  
// compile with: cl /EHsc /LD LNK2019g.cpp  
#include "windows.h"  
// WCHAR resolves to wchar_t  
__declspec(dllexport) void func(WCHAR*) {}  
```  
  
 下面的示例在上一示例中，使用 DLL 并生成 LNK2019，原因是类型 unsigned short * 和 WCHAR\*不相同。  
  
```cpp  
// LNK2019h.cpp  
// compile by using: cl /EHsc LNK2019h LNK2019g.lib  
// LNK2019 expected  
__declspec(dllimport) void func(unsigned short*);  
  
int main() {  
   func(0);  
}  
```  
  
 若要解决此错误，请更改`unsigned short`到`wchar_t`或`WCHAR`，或通过使用编译 LNK2019g.cpp **/Zc:wchar_t-**。
