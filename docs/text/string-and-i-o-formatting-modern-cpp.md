---
title: 字符串和 I/O 格式化（现代 C++）
description: 适用于新式C++中可用的格式化字符串 i/o 的选项。
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: facb0b62cc1e92ed09a9ba729d766e5db7404282
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 11/21/2019
ms.locfileid: "74308185"
---
# <a name="string-and-io-formatting-modern-c"></a>字符串和 I/O 格式化（现代 C++）

C++[\<iostream >](../standard-library/iostream.md)类、函数和运算符支持格式化的字符串 i/o。 例如，下面的代码演示如何将 `cout` 设置为将整数格式化为十六进制输出。 首先，它会保存当前状态以便以后重置，因为一旦将格式状态传递到 `cout`，它将一直保持此状态，直到发生更改。 它不只适用于一行代码。

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

此方法是类型安全且可扩展的，但它也很复杂且更详细。

## <a name="alternative-format-options"></a>替代格式选项

作为替代方法，你可以使用 `Boost.Format` C++ ，即使它是非标准的。 你可以下载从任何 Boost 库[Boost](https://www.boost.org/)网站。

`Boost.Format` 的一些优点如下：

- Safe：类型安全，并引发错误的异常，例如规范太少或过多的项。

- 可扩展：适用于可进行流式处理的任何类型。

- 便利：标准 Posix 和类似格式字符串。

尽管 `Boost.Format` 是基于C++ [\<iostream >](../standard-library/iostream-programming.md)设施构建的，但这些设施是安全且可扩展的，它们不能优化性能。 当需要优化性能时，请考虑使用 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，它们高效且易于使用。 但是，它们不是可扩展的，也不是安全的。 （存在安全版本，但会导致性能略微下降。 有关详细信息，请参阅[printf_s、 _printf_s_l、 wprintf_s、 _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、 _sprintf_s_l、 swprintf_s、 _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)。

以下代码演示了某些 Boost 格式功能特点。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>另请参阅

[欢迎返回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++ 语言参考](../cpp/cpp-language-reference.md)<br/>
[C++ 标准库](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
