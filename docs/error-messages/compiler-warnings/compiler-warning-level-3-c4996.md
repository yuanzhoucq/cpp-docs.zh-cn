---
title: 编译器警告 （等级 3） C4996
ms.date: 11/17/2017
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: cbb93bdba5853ed47bc3326d47bbb3c65ad7ce41
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472171"
---
# <a name="compiler-warning-level-3-c4996"></a>编译器警告 （等级 3） C4996

编译器遇到弃用声明。 **此警告始终是有意消息来自的库或包含的头文件，不应在不了解后果的情况下使用不推荐使用的符号的作者。** 不推荐使用修饰符或特性声明的站点上指定实际的警告消息。

这些是由 C 运行时库和标准库，但未详尽列出生成的一些常见 C4996 消息。 可单击的链接，或继续阅读，以解决此问题，或若要关闭该警告的方式。

- [此项的 POSIX 名称已弃用。请改用与 ISO C 和 c + + 一致的名称： *new_name*。请参阅联机帮助了解详细信息。](#posix-function-names)

- [此函数或变量可能不安全。请考虑使用*safe_version*相反。若要禁用弃用，请使用\_CRT\_SECURE\_NO\_WARNINGS。请参阅联机帮助了解详细信息。](#unsafe-crt-library-functions)

- [std::*function_name*::\_选中此项\_迭代器::\_Deprecate 调用到 std::*function_name*可能不安全的参数与此调用依靠调用方检查传递的值正确。若要禁用此警告，请使用 -D_SCL_SECURE_NO_WARNINGS。有关如何使用 Visual c + + Checked Iterators，请参阅文档](#unsafe-standard-library-functions)

- [此函数或变量已被较新的库或操作系统功能。请考虑使用*new_item*相反。请参阅联机帮助了解详细信息。](#obsolete-crt-functions-and-variables)

## <a name="cause"></a>原因

当编译器遇到函数或变量标记为时发生 C4996[弃用](../../cpp/deprecated-cpp.md)通过使用`__declspec(deprecated)`修饰符，或当你尝试访问的函数、 类成员或具有 C + + 14 的 typedef [ \[\[弃用\]\] ](../../cpp/attributes.md)属性。 可以使用`__declspec(deprecated)`修饰符或`[[deprecated]]`自己属性中你的库或标头文件来警告你有关已弃用的函数、 变量、 成员或类型定义的客户端。

## <a name="remarks"></a>备注

许多函数、 成员函数，模板函数和 Visual Studio 中的库中的全局变量标记为*弃用*。 这些函数已弃用，因为它们可能具有不同的首选的名称，可能不安全或更安全的变体，或可能已过时。 许多弃用消息包括不推荐使用的函数或全局变量的建议的替换。

若要解决此问题，我们通常建议更改代码以改为使用建议的更安全的或更新函数和全局变量。 如果您需要使用现有的函数或变量出于可移植性原因，可以关闭该警告。

### <a name="to-turn-the-warning-off-without-fixing-the-issue"></a>要关闭该警告而不解决此问题

可以通过使用来关闭的警告的特定代码行[警告](../../preprocessor/warning.md)杂注， `#pragma warning(suppress : 4996)`。 也可以关闭该警告文件中通过使用警告杂注， `#pragma warning(disable : 4996)`。

您可以关闭该警告全局命令行生成中使用 **/wd4996**命令行选项。

若要关闭的警告的 Visual Studio IDE 中的整个项目：

- 打开**属性页**对话框为您的项目。 有关如何使用属性页对话框的信息，请参阅[属性页](../../ide/property-pages-visual-cpp.md)。
- 选择**配置属性**， **C/c + +**，**高级**页。
- 编辑**禁用特定警告**属性来添加`4996`。 选择**确定**应用所做的更改。

此外可以使用预处理器宏关闭弃用警告库中使用某些特定类。 下面描述了这些宏。

若要在 Visual Studio 中定义预处理器宏：

- 打开**属性页**对话框为您的项目。 有关如何使用属性页对话框的信息，请参阅[属性页](../../ide/property-pages-visual-cpp.md)。
- 展开**配置属性 > C/c + + > 预处理器**。
- 在中**预处理器定义**属性，添加宏名称。 选择“确定”  进行保存，然后重新生成项目。

若要仅在特定源文件中定义的宏，请添加一个行如`#define EXAMPLE_MACRO_NAME`包含的头文件的任意行之前。

## <a name="specific-c4996-messages"></a>特定 C4996 消息

以下是一些常见 C4996 警告和错误的源。

### <a name="posix-function-names"></a>POSIX 函数名称

**此项的 POSIX 名称已弃用。请改用与 ISO C 和 c + + 一致的名称：** *new_name*。 **请参阅联机帮助了解详细信息。**

Microsoft 已重命名以符合 C99 和 c++03 规则的实现定义的全局函数名称的 CRT 中的一些 POSIX 函数。 仅原始 POSIX 名称已弃用，而不是函数本身。 在大多数情况下，前导下划线已添加到 POSIX 函数名称，以创建符合标准的名称。 编译器会发出弃用警告的原始函数名称，并建议首选的名称。

若要解决此问题，我们通常建议更改代码以改为使用建议的函数名称。 但是，更新的名称是特定于 Microsoft 的。 如果您需要将现有的函数名称，用于可移植性原因，可以关闭这些警告。 在其原始名称下的库中的 POSIX 函数现在仍然有效。

若要关闭这些函数的弃用警告，请定义预处理器宏 **\_CRT\_NONSTDC\_NO\_WARNINGS**。 可以通过包括选项定义此宏在命令行`/D_CRT_NONSTDC_NO_WARNINGS`。

### <a name="unsafe-crt-library-functions"></a>不安全的 CRT 库函数

**此函数或变量可能不安全。请考虑使用** *safe_version* **相反。若要禁用弃用，请使用\_CRT\_SECURE\_NO\_WARNINGS。请参阅联机帮助了解详细信息。**

Microsoft 已弃用某些 CRT 和 c + + 标准库函数和全局变量以支持更多安全版本。 在大多数情况下，已弃用的函数允许未选中状态的读取或写入访问权限可能会导致严重的安全问题的缓冲区。 编译器会发出对这些函数的弃用警告，并建议首选函数。

若要解决此问题，我们建议你使用的函数或变量*safe_version*相反。 如果已验证不能为缓冲区覆盖或 overread 出现在你的代码，并且您不能更改的代码可移植性原因，您可以关闭该警告。

若要关闭 CRT 中的这些函数的弃用警告，定义 **\_CRT\_SECURE\_NO\_WARNINGS**。 若要关闭有关弃用的全局变量的警告，请定义 **\_CRT\_SECURE\_NO\_WARNINGS\_GLOBALS**。 有关这些不推荐使用的函数和全局变量的详细信息，请参阅[CRT 中的安全功能](../../c-runtime-library/security-features-in-the-crt.md)并[安全库： c + + 标准库](../../standard-library/safe-libraries-cpp-standard-library.md)。

### <a name="unsafe-standard-library-functions"></a>不安全的标准库函数

__std::__*function_name*__::\_选中此项\_迭代器::\_Deprecate 调用到 std::__*function_name***可能不安全的参数与此调用依靠调用方检查传递的值是否正确。若要禁用此警告，请使用-D\_SCL\_SECURE\_NO\_WARNINGS。有关如何使用 Visual c + + Checked Iterators，请参阅文档**

因为某些 c + + 标准库模板函数不会检查参数正确，在调试版本中会出现此警告。 在大多数情况下，这是因为没有足够的信息可供要检查容器边界的函数或使用该函数可能会错误地使用迭代器。 此警告有助于标识这些函数用途，因为它们可能会在程序中的严重安全漏洞的源。 有关更多信息，请参见 [Checked Iterators](../../standard-library/checked-iterators.md)。

例如，会出现此警告在调试模式下如果传递到的元素指针`std::copy`而不是普通的数组。 若要解决此问题，请使用正确声明的数组，因此库可以检查数组扩展盘区，并执行边界检查。

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

多个标准库算法已更新，可以在 C + + 14 中有"双范围"版本。 如果您使用双范围版本，第二个范围提供了必要的边界检查：

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

此示例演示几个标准库可用于检查迭代器使用情况的更多方法和未选中状态的使用情况可能存在危险：

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

如果已验证您的代码不能具有缓冲区溢出错误在标准库函数，触发此警告，你可能想要关闭此警告。 若要关闭这些函数的警告，定义 **\_SCL\_SECURE\_NO\_WARNINGS**。

### <a name="checked-iterators-enabled"></a>检查迭代器启用

如果使用编译时不使用经检查迭代器，也可能发生 C4996`_ITERATOR_DEBUG_LEVEL`定义为 1 或 2。 设置为 2，默认情况下，对于调试模式生成，并为 0 表示零售版本。 有关更多信息，请参见 [Checked Iterators](../../standard-library/checked-iterators.md) 。

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

### <a name="unsafe-mfc-or-atl-code"></a>不安全的 MFC 或 ATL 代码

如果您出于安全原因使用不推荐使用的 MFC 或 ATL 函数，也可能发生 C4996。

若要解决此问题，我们强烈建议你更改代码以改为使用更新后的函数。

有关如何禁用这些警告的信息，请参阅[_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings)。

### <a name="obsolete-crt-functions-and-variables"></a>已过时的 CRT 函数和变量

**此函数或变量已被较新的库或操作系统功能。请考虑使用** *new_item* **相反。请参阅联机帮助了解详细信息。**

某些库函数和全局变量由于过时已弃用。 可能会在未来版本的库中删除这些函数和变量。 编译器会发出对这些项的弃用警告，并建议首选备用项。

若要解决此问题，我们建议更改代码以使用建议的函数或变量。

若要关闭这些项的弃用警告，定义 **\_CRT\_过时\_NO\_WARNINGS**。 有关详细信息，请参阅弃用的函数或变量的文档。

### <a name="marshalling-errors-in-clr-code"></a>CLR 代码中的封送处理错误

使用 CLR 封送处理库时，也会发生 C4996。 在这种情况下，C4996 是错误，而非警告。 使用时，会发生此错误[marshal_as](../../dotnet/marshal-as.md)要求的两个数据类型之间进行转换[marshal_context 类](../../dotnet/marshal-context-class.md)。 当封送处理库不支持转换，也可能收到此错误。 有关封送处理库的详细信息，请参阅 [Overview of Marshaling in C++](../../dotnet/overview-of-marshaling-in-cpp.md)。

此示例生成 C4996，因为封送处理库需要上下文才能将从转换`System::String`到`const char *`。

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

## <a name="example-user-defined-deprecated-function"></a>示例： 用户定义的已弃用的函数

可以在你自己的代码中使用不推荐使用的属性时不再推荐使用的某些函数发出警告的调用方。 在此示例中，为在其中被否决的函数声明，在行和在其使用该函数的行生成 C4996。

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
