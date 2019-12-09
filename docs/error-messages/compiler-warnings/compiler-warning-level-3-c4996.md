---
title: 编译器警告（等级3） C4996
description: 说明为什么会发生编译器警告 C4996，并说明如何处理该警告。
ms.date: 11/25/2019
f1_keywords:
- C4996
helpviewer_keywords:
- C4996
ms.assetid: 926c7cc2-921d-43ed-ae75-634f560dd317
ms.openlocfilehash: 98662dc0b5439c1f8857e4f2ad259793a4d03e41
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898780"
---
# <a name="compiler-warning-level-3-c4996"></a>编译器警告（等级3） C4996

你的代码使用标记为已*弃用*的函数、类成员、变量或 typedef。 不推荐使用[__declspec （不推荐使用）](../../cpp/deprecated-cpp.md)修饰符或 c + + 14\[\[不推荐使用的符号[\]\]](../../cpp/attributes.md)特性。 实际的 C4996 警告消息由声明的 `deprecated` 修饰符或特性指定。

> [!IMPORTANT]
> 此警告始终是来自声明符号的标头文件的作者的故意消息。 不要在不了解后果的情况下使用已弃用的符号。

## <a name="remarks"></a>备注

Visual Studio 库中的许多函数、成员函数、模板函数和全局变量已*弃用*。 有些，例如 POSIX 和 Microsoft 特定的函数，因为它们现在具有不同的首选名称。 某些 C 运行时库函数被弃用，因为它们不安全，并且具有更安全的变体。 其他内容已被弃用，因为它们已过时。 弃用消息通常包含推荐的替代函数或全局变量。

## <a name="turn-off-the-warning"></a>关闭警告

为了解决 C4996 问题，我们通常建议您更改代码。 请改用建议的函数和全局变量。 如果出于可移植性原因需要使用现有函数或变量，则可以关闭警告。

若要关闭特定代码行的警告，请使用[警告](../../preprocessor/warning.md)杂注，`#pragma warning(suppress : 4996)`。

若要关闭文件中的警告，请使用警告杂注，`#pragma warning(disable : 4996)`。

若要在命令行生成中全局关闭警告，请使用[/wd4996](../../build/reference/compiler-option-warning-level.md)命令行选项。

若要在 Visual Studio IDE 中关闭整个项目的警告：

1. 打开项目的 "**属性页**" 对话框。 有关如何使用 "属性页" 对话框的信息，请参阅[属性页](../../build/reference/property-pages-visual-cpp.md)。

1. 选择 "**配置属性**" > **CC++ /**  > "**高级**" 页。

1. 编辑 "**禁用特定警告**" 属性以添加 `4996`。 选择 **"确定"** 以应用所做的更改。

你还可以使用预处理器宏来关闭库中使用的某些特定类的弃用警告。 下面描述了这些宏。

在 Visual Studio 中定义预处理器宏：

1. 打开项目的 "**属性页**" 对话框。 有关如何使用 "属性页" 对话框的信息，请参阅[属性页](../../build/reference/property-pages-visual-cpp.md)。

1. 展开 "**配置属性" >C++ C/> 预处理器**。

1. 在 "**预处理器定义**" 属性中，添加宏名称。 选择“确定” 进行保存，然后重新生成项目。

若要仅在特定源文件中定义宏，请在包含头文件的任何行之前添加一行，如 `#define EXAMPLE_MACRO_NAME`。

下面是 C4996 警告和错误的一些常见源：

## <a name="posix-function-names"></a>POSIX 函数名称

**此项的 POSIX 名称已弃用。改为使用 ISO C++ C 和相容名称：** "*新名称*"。 **有关详细信息，请参阅联机帮助。**

Microsoft 在 CRT 中重命名了某些 POSIX 和 Microsoft 特定的库函数，以符合 C99 和 c + + 03 对保留和全局实现定义名称的约束。 *只会弃用名称，而不会弃用函数本身*。 在大多数情况下，向函数名称添加了前导下划线来创建一致的名称。 编译器会发出对原始函数名称的弃用警告，并建议首选名称。

若要解决此问题，我们通常建议改为改用建议的函数名称。 但是，更新的名称是 Microsoft 特定的。 如果需要使用现有函数名称以实现可移植性，则可以关闭这些警告。 函数在库中的原始名称下面仍可用。

若要关闭这些函数的弃用警告，请定义预处理器宏 **\_CRT\_NONSTDC\_NO\_WARNINGS**。 可以通过在命令行中包含选项 `/D_CRT_NONSTDC_NO_WARNINGS`来定义此宏。

## <a name="unsafe-crt-library-functions"></a>不安全的 CRT 库函数

**此函数或变量可能不安全。请考虑**改用*安全版本* **。若要禁用弃用，请使用 \_CRT\_安全\_不\_警告。 有关详细信息，请参阅联机帮助。**

Microsoft 弃用了某些 CRT C++和标准库函数和全局函数，因为提供了更安全的版本。 大多数不推荐使用的函数允许对缓冲区进行未检查的读取或写入访问。 它们可能会导致严重的安全问题。 编译器会发出对这些函数的弃用警告，并建议首选函数。

若要解决此问题，建议改为使用函数或变量的*安全版本*。 有时您无法实现可移植性或向后兼容性的原因。 仔细验证代码中是否存在缓冲区覆盖或 overread 的情况。 然后，可以关闭警告。

若要关闭 CRT 中的这些函数的弃用警告，定义 **\_CRT\_SECURE\_NO\_WARNINGS**。

若要关闭有关弃用的全局变量的警告，请将 **\_CRT 定义\_安全\_不\_警告\_全局**。

有关这些弃用的函数和全局函数的详细信息，请参阅 CRT 和安全库[中的安全功能](../../c-runtime-library/security-features-in-the-crt.md) [ C++ ：标准库](../../standard-library/safe-libraries-cpp-standard-library.md)。

## <a name="unsafe-standard-library-functions"></a>不安全的标准库函数

__"std：：__ *function_name* __：：\_Unchecked\_迭代器：：\_弃用" 对 Std：：__ *function_name* **的调用，其中包含可能不安全的参数-此调用依赖于调用方来检查传递的值是否正确。若要禁用此警告，请使用-D\_SCL\_SECURE\_不\_警告。请参阅有关如何使用视觉对象C++ "检查迭代器" 的文档**

调试版本中会出现此警告， C++因为某些标准库模板函数不会检查参数的正确性。 通常，这是因为函数提供的信息不足以检查容器界限。 或，因为迭代器可能会对函数错误地使用。 此警告有助于识别这些功能，因为它们可能是程序中严重安全漏洞的来源。 有关详细信息，请参阅[检查迭代](../../standard-library/checked-iterators.md)器。

例如，如果将元素指针传递到 `std::copy`而不是纯数组，则此警告会在调试模式下出现。 若要解决此问题，请使用适当声明的数组，使库可以检查阵列范围并执行边界检查。

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

多个标准库算法已更新为具有 c + + 14 中的 "双重范围" 版本。 如果使用的是双重范围版本，第二个范围提供必要的边界检查：

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

此示例演示了如何使用标准库来检查迭代器的使用情况，并说明了在未检查的使用情况下可能很危险：

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

如果已验证你的代码不能出现缓冲区溢出错误，则可以关闭此警告。 若要关闭这些函数的警告，定义 **\_SCL\_SECURE\_NO\_WARNINGS**。

## <a name="checked-iterators-enabled"></a>已启用检查迭代器

如果 `_ITERATOR_DEBUG_LEVEL` 定义为1或2，则也可能会发生 C4996。 对于调试模式生成，默认设置为 2; 对于零售版本，它设置为0。 有关详细信息，请参阅[检查迭代](../../standard-library/checked-iterators.md)器。

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

## <a name="unsafe-mfc-or-atl-code"></a>不安全 MFC 或 ATL 代码

如果出于安全原因使用了不推荐使用的 MFC 或 ATL 函数，则可能会发生 C4996。

若要解决此问题，我们强烈建议您更改代码以改用更新后的函数。

有关如何禁止显示这些警告的信息，请参阅[_AFX_SECURE_NO_WARNINGS](../../mfc/reference/diagnostic-services.md#afx_secure_no_warnings)。

## <a name="obsolete-crt-functions-and-variables"></a>过时的 CRT 函数和变量

**此函数或变量已被较新的库或操作系统功能取代。请考虑**改用*new_item* **。有关详细信息，请参阅联机帮助。**

某些库函数和全局变量由于过时已弃用。 可能会在未来版本的库中删除这些函数和变量。 编译器会发出对这些项的弃用警告，并建议首选备用项。

若要解决此问题，我们建议更改代码以使用建议的函数或变量。

若要关闭这些项的弃用警告，定义 **\_CRT\_过时\_NO\_WARNINGS**。 有关详细信息，请参阅弃用的函数或变量的文档。

## <a name="marshaling-errors-in-clr-code"></a>在 CLR 代码中封送处理错误

使用 CLR 封送处理库时也可能会发生 C4996。 在这种情况下，C4996 是错误，而非警告。 当使用[marshal_as](../../dotnet/marshal-as.md)在需要[marshal_context 类](../../dotnet/marshal-context-class.md)的两个数据类型之间进行转换时，将发生此错误。 如果封送处理库不支持转换，也会收到此错误。 有关封送处理库的详细信息，请参阅[中C++的封送处理概述](../../dotnet/overview-of-marshaling-in-cpp.md)。

此示例将生成 C4996，因为封送处理库需要上下文才能从 `System::String` 转换为 `const char *`。

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

## <a name="example-user-defined-deprecated-function"></a>示例：用户定义的不推荐使用的函数

您可以在您自己的代码中使用不推荐使用的属性，以便在您不再建议使用某些函数时警告调用方。 在此示例中，C4996 是在两个位置生成的：一个用于已声明的不推荐使用的函数，另一个用于使用函数的行。

```cpp
// C4996.cpp
// compile with: /W3
// C4996 warning expected
#include <stdio.h>

// #pragma warning(disable : 4996)
void func1(void) {
   printf_s("\nIn func1");
}

[[deprecated]]
void func1(int) {
   printf_s("\nIn func2");
}

int main() {
   func1();
   func1(1);    // C4996
}
```
