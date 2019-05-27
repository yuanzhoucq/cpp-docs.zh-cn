---
title: 字符串和 I-O 格式化 (现代C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: c051a7d70042456d30bee0ebb2b362c5d05b8e37
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266915"
---
# <a name="string-and-io-formatting-modern-c"></a>字符串和 I/O 格式化（现代 C++）

C++ [iostreams](../standard-library/iostream.md)善于处理格式化字符串 I/O。 例如，下面的代码演示如何设置 cout 来格式化一个整数，使其输出为十六进制数，先保存当前状态，再在以后重新设置，因为一旦状态格式传递给 cout，它将始终处于这种状态，直到被更改为止，而不是仅应用于那一行代码。

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex
        << uppercase
        << setw(8)
        << setfill('0')
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

这在许多情况下是非常麻烦的。 作为替代方法，可以从Boost C++ 库中，使用 Boost.Format, 尽管这并非标准方法。 可以从[Boost](http://www.boost.org/)网站下载任何 Boost 库。

Boost.Format 的一些优点包括：

- 安全：类型安全的则会引发异常的错误 — 例如，太少或过多项规范。

- 可扩展：适用于可进行流处理任何类型。

- 方便：标准 Posix 以及类似的格式字符串。

虽然 Boost.Format 基于 C++ [iostreams](../standard-library/iostream-programming.md)，并且它们是安全且可扩展的，但它们不能优化性能。 当需要优化性能时，请考虑使用 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，它们高效且易于使用。 但它们不可扩展，也无法抵御漏洞 （存在安全版本，但会导致性能略微下降。 有关详细信息，请参阅[printf_s、 _printf_s_l、 wprintf_s、 _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、 _sprintf_s_l、 swprintf_s、 _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)。

以下代码演示了某些 Boost 格式功能特点。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>请参阅

[欢迎回到 C++（现代 C++）](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
