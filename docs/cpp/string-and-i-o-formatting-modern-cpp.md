---
title: 字符串和 I/O 格式化（现代 C++）
description: 现代版中的格式化字符串 I/O 可用的选项C++。
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: e22c745798109a2dbef82297c45256593823f806
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/31/2019
ms.locfileid: "66450503"
---
# <a name="string-and-io-formatting-modern-c"></a>字符串和 I/O 格式化（现代 C++）

C++[ \<iostream >](../standard-library/iostream.md)类、 函数和运算符支持格式化的字符串 I/O。 例如，下面的代码演示如何设置`cout`设置整数的输出以十六进制格式的格式。 首先，它将保存当前的状态重置之后，因为一次传递到格式状态`cout`，保持此方式直到改变。 它只是不能应用于一个代码行。

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

这种方法是类型安全、 可扩展的但它也是复杂和冗长。

## <a name="alternative-format-options"></a>备用格式选项

作为替代方法，你可以使用`Boost.Format`Boost 中C++库，即使是非标准的。 可以从[Boost](https://www.boost.org/)网站下载任何 Boost 库。

一些优势`Boost.Format`是：

- 安全：类型安全，则引发错误异常，例如，太少或过多项规范。

- 可扩展：适用于可进行流处理任何类型。

- 方便：标准 Posix 以及类似的格式字符串。

尽管`Boost.Format`基于C++ [ \<iostream >](../standard-library/iostream-programming.md)设备，它们都是安全且可扩展，它们不是性能优化。 当需要优化性能时，请考虑使用 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)，它们高效且易于使用。 但是，它们不可扩展或安全漏洞。 （存在安全版本，但会导致性能略微下降。 有关详细信息，请参阅[printf_s、 _printf_s_l、 wprintf_s、 _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、 _sprintf_s_l、 swprintf_s、 _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)。

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
