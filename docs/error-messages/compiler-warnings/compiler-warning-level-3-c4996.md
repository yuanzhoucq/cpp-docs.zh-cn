---
title: "编译器警告 （等级 3） C4996 |Microsoft 文档"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4996
dev_langs:
- C++
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
caps.latest.revision: 34
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 128bd124c2536d86c8b673b54abc4b5505526b41
ms.openlocfilehash: 9a0c25772fadec86a893b8c7c4af09072eb0476f
ms.contentlocale: zh-cn
ms.lasthandoff: 05/10/2017

---
# <a name="compiler-warning-level-3-c4996"></a>编译器警告 （等级 3） C4996
编译器遇到弃用声明。  
  
此警告或错误可能有几种含义，具体取决于上下文。  
  
当编译器遇到函数或被标记为的变量，则会发生 C4996[弃用](../../cpp/deprecated-cpp.md)使用`__declspec(deprecated)`修饰符。 当您尝试访问函数、 类成员或具有 C + + 14 的 typedef 时，还将发出此警告`[[deprecated]]`属性。 有关详细信息，请参阅[c + + 标准特性](../../cpp/attributes2.md)。 你可以使用此属性自己中你的库来警告你有关已弃用的函数、 成员或 typedef 的客户端。  
  
多个函数、成员函数、模板函数和 Visual Studio 的库中的全局变量标记为已弃用。 这些函数可能具有不同的首选名称，可能不安全或具有更加安全的变体，或可能已过时。 许多错误消息包括不推荐使用的函数或全局变量的建议的替换。  
  
若要解决此问题，我们通常建议你更改代码以改为使用建议的更安全的或更新函数和全局变量。 如果你需要使用现有的函数或变量，可移植性原因，可以关闭该警告。  
  
你可以通过将关闭的警告的代码的特定行[警告](../../preprocessor/warning.md)杂注`#pragma warning(suppress : 4996)`。 你可以将其关闭文件中使用警告杂注`#pragma warning(disable : 4996)`。 你可以将其关闭全局在命令行版本中使用**/wd4996**命令行选项。 若要关闭的警告的 Visual Studio IDE 中的项目，打开**属性页**对话框中，选择**配置属性**， **C/c + +**，**高级**页上，编辑**禁用特定警告**属性来添加`4996`。  你可以使用预处理器宏关闭弃用警告在库中使用的某些特定的类。 下面介绍了这些宏。  
  
以下是一些 C4996 的库源。  
  
## <a name="posix-function-names"></a>POSIX 函数名称  
  
**此项的 POSIX 名称已弃用。请改用 ISO C 和 c + + 一致的名称︰** *new_name*。 **请参阅联机帮助的详细信息。**  
  
Microsoft 已重命名以符合 C99 和 C + + 03 规则实现定义的全局函数名称的 CRT 中的一些 POSIX 函数。 仅的原始 POSIX 名称已被否决，函数本身。 在大多数情况下，前导下划线已添加到 POSIX 函数名称，以创建符合标准的名称。 编译器会发出弃用警告原始函数名称，并建议首选的名称。  
  
若要解决此问题，我们通常建议你更改代码以改为使用建议的函数名称。 但是，更新的名称是特定于 Microsoft 的。 如果你需要使用现有的函数名称，出于可移植性原因，你可以关闭这些警告。 在其原始名称下库仍然提供了 POSIX 函数。  
  
若要关闭这些函数的弃用警告，请定义预处理器宏 **_CRT_NONSTDC_NO_WARNINGS**。 你可以通过包括选项 `/D_CRT_NONSTDC_NO_WARNINGS`在命令行定义此宏。 若要在 Visual Studio 中定义此宏，请打开项目的  “属性页”对话框。 展开“配置属性” 、“C/C++” 、“预处理器” 。 在“预处理器定义” 中，添加 `_CRT_NONSTDC_NO_WARNINGS`。 选择“确定”  进行保存，然后重新生成项目。 若要仅在特定源文件中定义此宏，请将行 `#define _CRT_NONSTDC_NO_WARNINGS` 添加到包括标头文件的任意行之前。  
  
## <a name="unsafe-crt-library-functions"></a>不安全的 CRT 库函数  
  
 **此函数或变量可能不安全。请考虑使用***safe_version* **相反。  若要禁用弃用，请使用 _CRT_SECURE_NO_WARNINGS。请参阅联机帮助了解详细信息。**  
  
 Microsoft 已弃用某些 CRT 和 c + + 标准库函数和全局函数，为支持更多安全版本。 在大多数情况下，已弃用的函数允许未选中的读取或写入访问权限会导致严重的安全问题的缓冲区。 编译器会发出对这些函数的弃用警告，并建议首选函数。  
  
 若要解决此问题，我们建议你使用的函数或变量*safe_version*相反。 如果已验证不可能缓冲区覆盖或者 overread 出现在代码中，并且你不能更改的代码可移植性原因，你可以关闭该警告。  
   
 若要在 CRT 中关闭这些函数的弃用警告，请定义 **_CRT_SECURE_NO_WARNINGS**。 若要关闭有关弃用的全局变量的警告，请定义 **_CRT_SECURE_NO_WARNINGS_GLOBALS**。 有关这些不推荐使用的函数和全局变量的详细信息，请参阅[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)和[安全库︰ c + + 标准库](../../standard-library/safe-libraries-cpp-standard-library.md)。  
  
## <a name="unsafe-standard-library-functions"></a>不安全的标准库函数  
  
 **std::** *function_name* **::\_未选中\_迭代器::\_Deprecate 调用 std::** *function_name* **可能不安全的参数与此调用依靠调用方检查传递的值是否正确。若要禁用此警告，请使用 -D_SCL_SECURE_NO_WARNINGS。有关如何使用 Visual c + + 检查迭代器，请参阅文档**  
  
由于某些 c + + 标准库模板函数不会检查参数的正确性，在调试版本中会出现此警告。 在大多数情况下，这是因为没有足够的信息是到函数，以检查容器边界可用或者可能使用的函数不正确地使用迭代器。 此警告有助于标识这些函数用途，因为它们可能会在程序中的安全漏洞的源。 有关更多信息，请参见 [Checked Iterators](../../standard-library/checked-iterators.md)。  
  
例如，此警告将出现在调试模式下如果传递到非元素指针`std::copy`而不是普通数组。 若要解决此问题，请使用正确声明的数组，因此库可以检查数组范围并执行边界检查。  
  
```cpp  
// C4996_copyarray.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_copyarray.cpp
#include <algorithm>
 
void example(char const * const src) { 
    char dest[1234]; 
    char * pdest3 = dest + 3;
    std::copy(src, src + 42, pdest3); // C4996 
    std::copy(src, src + 42, dest);   // OK, copy can tell that dest is 1234 elements 
} 
```  
  
几种标准库算法已更新，可在 C + + 14 中有"双范围"版本。 如果你使用双范围版本，第二个范围提供必要的边界检查︰  
  
```cpp  
// C4996_containers.cpp
// compile with: cl /c /W4 /D_DEBUG C4996_containers.cpp
#include <algorithm>
 
bool example(
    char const * const left, 
    const size_t leftSize, 
    char const * const right, 
    const size_t rightSize) 
{ 
    bool result = false;
    result = std::equal(left, left + leftSize, right); // C4996
    // To fix, try this form instead: 
    // result = std::equal(left, left + leftSize, right, right + rightSize); // OK 
    return result;
}
```  
  
此示例演示几种标准库可用于检查迭代器使用情况的更多方式和时未选中的使用情况可能会十分危险︰  
  
```cpp  
// C4996_standard.cpp
// compile with: cl /EHsc /W4 /MDd C4996_standard.cpp
#include <algorithm>  
#include <array>  
#include <iostream>  
#include <iterator>  
#include <numeric>  
#include <string>  
#include <vector>  
  
using namespace std;  
  
template <typename C> void print(const string& s, const C& c) {  
    cout << s;  
  
    for (const auto& e : c) {  
        cout << e << " ";  
    }  
  
    cout << endl;  
}  
  
int main()  
{  
    vector<int> v(16);  
    iota(v.begin(), v.end(), 0);  
    print("v: ", v);  
  
    // OK: vector::iterator is checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    vector<int> v2(16);  
    transform(v.begin(), v.end(), v2.begin(), [](int n) { return n * 2; });  
    print("v2: ", v2);  
  
    // OK: back_insert_iterator is marked as checked in debug mode  
    // (i.e. an overrun is impossible)  
    vector<int> v3;  
    transform(v.begin(), v.end(), back_inserter(v3), [](int n) { return n * 3; });  
    print("v3: ", v3);  
  
    // OK: array::iterator is checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    array<int, 16> a4;  
    transform(v.begin(), v.end(), a4.begin(), [](int n) { return n * 4; });  
    print("a4: ", a4);  
  
    // OK: Raw arrays are checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    // NOTE: This applies only when raw arrays are 
    // given to C++ Standard Library algorithms!  
    int a5[16];  
    transform(v.begin(), v.end(), a5, [](int n) { return n * 5; });  
    print("a5: ", a5);  
  
    // WARNING C4996: Pointers cannot be checked in debug mode  
    // (i.e. an overrun triggers undefined behavior)  
    int a6[16];  
    int * p6 = a6;  
    transform(v.begin(), v.end(), p6, [](int n) { return n * 6; });  
    print("a6: ", a6);  
  
    // OK: stdext::checked_array_iterator is checked in debug mode  
    // (i.e. an overrun triggers a debug assertion)  
    int a7[16];  
    int * p7 = a7;  
    transform(v.begin(), v.end(), 
        stdext::make_checked_array_iterator(p7, 16), 
        [](int n) { return n * 7; });  
    print("a7: ", a7);  
  
    // WARNING SILENCED: stdext::unchecked_array_iterator 
    // is marked as checked in debug mode, but it performs no checking, 
    // so an overrun triggers undefined behavior  
    int a8[16];  
    int * p8 = a8;  
    transform( v.begin(), v.end(), 
        stdext::make_unchecked_array_iterator(p8), 
        [](int n) { return n * 8; });  
    print("a8: ", a8);  
}  
```  
  
如果已验证你的代码不能具有出现缓冲区溢出触发此警告的标准库函数中的错误，你可能想要关闭此警告。 若要关闭这些函数的警告，请定义 **_SCL_SECURE_NO_WARNINGS**。   
  
## <a name="example-checked-iterators-enabled"></a>示例︰ 检查迭代器启用  
  
如果使用编译时不使用检查迭代器，也可能发生 C4996`_ITERATOR_DEBUG_LEVEL`定义为 1 或 2。 它被设置为默认情况下，对于调试模式生成的 2 和零售版本的 0。 有关更多信息，请参见 [Checked Iterators](../../standard-library/checked-iterators.md) 。  
  
```cpp  
// C4996_checked.cpp  
// compile with: /EHsc /W4 /MDd C4996_checked.cpp  
#define _ITERATOR_DEBUG_LEVEL 2  
  
#include <algorithm>  
#include <iterator>  
  
using namespace std;  
using namespace stdext;  
  
int main() {  
    int a[] = { 1, 2, 3 };  
    int b[] = { 10, 11, 12 };  
    copy(a, a + 3, b + 1);   // C4996  
    // try the following line instead:  
    // copy(a, a + 3, checked_array_iterator<int *>(b, 3));   // OK  
}  
```  
  
## <a name="unsafe-mfc-or-atl-code"></a>不安全的 MFC 或 ATL 代码  
  
如果出于安全原因使用了否决的 MFC 或 ATL 函数，也可能发生 C4996。  
  
若要解决此问题，我们强烈建议你更改代码以改为使用更新的函数。  
  
有关如何禁止显示这些警告的信息，请参阅[_afx_secure_no_warnings，则](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings)和[_ATL_SECURE_NO_WARNINGS](http://msdn.microsoft.com/Library/587d29d8-a75a-44a3-bec8-f724087e5e73)。  
  
## <a name="obsolete-crt-functions-and-variables"></a>过时的 CRT 函数和变量  
  
**此函数或变量已被较新的库或操作系统功能取代。请考虑使用** *new_item* **相反。请参阅联机帮助了解详细信息。**  
  
某些库函数和全局变量由于过时已弃用。 可能会在未来版本的库中删除这些函数和变量。 编译器会发出对这些项的弃用警告，并建议首选备用项。  
  
若要解决此问题，我们建议你更改代码以使用建议的函数或变量。  
  
若要关闭这些项的弃用警告，请定义 **_CRT_OBSOLETE_NO_WARNINGS**。 有关详细信息，请参阅弃用的函数或变量的文档。  
  
## <a name="example-marshalling-errors-in-clr-code"></a>示例︰ 封送处理 CLR 代码中的错误  
  
在使用 CLR 封送处理库时，也可能发生 C4996。 在这种情况下，C4996 是错误，而非警告。 当你使用，会出现此错误[marshal_as](../../dotnet/marshal-as.md)需要的两个数据类型之间进行转换[marshal_context 类](../../dotnet/marshal-context-class.md)。 当封送处理库不支持转换，您也可以收到此错误。 有关封送处理库的详细信息，请参阅 [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md)。  
  
此示例生成 C4996，因为封送处理库需要上下文才能从转换`System::String`到`const char *`。  
  
```cpp  
// C4996_Marshal.cpp  
// compile with: /clr   
// C4996 expected  
#include <stdlib.h>  
#include <string.h>  
#include <msclr\marshal.h>  
  
using namespace System;  
using namespace msclr::interop;  
  
int main() {  
   String^ message = gcnew String("Test String to Marshal");  
   const char* result;  
   result = marshal_as<const char*>( message );  
   return 0;  
}  
```
  
## <a name="example-user-defined-deprecated-function"></a>示例︰ 用户定义已弃用的函数  
  
可以在你自己的代码中使用不推荐使用的属性来警告时不再建议使用的某些函数的调用方。 在此示例中，在其使用该函数的行和已弃用的函数声明的行，将生成 C4996。  
  
```cpp  
// C4996.cpp  
// compile with: /W3  
// C4996 warning expected  
#include <stdio.h>  
  
// #pragma warning(disable : 4996)  
void func1(void) {  
   printf_s("\nIn func1");  
}  
  
__declspec(deprecated) void func1(int) {  
   printf_s("\nIn func2");  
}  
  
int main() {  
   func1();  
   func1(1);    // C4996  
}  
```  
  

