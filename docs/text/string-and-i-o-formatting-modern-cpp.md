---
title: 字符串和 I/O 格式化（现代 C++）
description: 格式化字符串 I/O 的选择在现代C++中可用。
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: a3fc93b0baf414759eb50c787c4057fb85dcb370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375777"
---
# <a name="string-and-io-formatting-modern-c"></a>字符串和 I/O 格式化（现代 C++）

C++ [ \<iostream>](../standard-library/iostream.md)类、函数和运算符支持格式化的字符串 I/O。 例如，以下代码演示如何设置`cout`以十六进制形式输出的整数格式。 首先，它保存当前状态以在之后重置它，因为一旦格式状态传递给`cout`，它将一直保持这种状态，直到更改。 它不仅仅适用于一行代码。

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

此方法类型安全且可扩展，但它也复杂而详细。

## <a name="alternative-format-options"></a>可选格式选项

作为替代方法，您可以使用`Boost.Format`Boost C++库，即使它不标准。 您可以从 Boost 网站下载任何[Boost](https://www.boost.org/)库。

一些优点`Boost.Format`是：

- 安全：类型安全，并引发错误的异常，例如，规格太少或太多项。

- 可扩展：适用于任何可以流式传输的类型。

- 方便：标准 POSIX 和类似的格式字符串。

虽然`Boost.Format`基于C++[\<物联网>](../standard-library/iostream-programming.md)设施，这些设施是安全和可扩展的，但它们没有经过性能优化。 当您需要性能优化时，请考虑 C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)和[sprintf，](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md)它们快速且易于使用。 但是，它们不能扩展或免受漏洞的攻击。 （存在安全版本，但它们会受到轻微的性能损失。 有关详细信息，请参阅[printf_s、_printf_s_l、wprintf_s、_wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md)和[sprintf_s、_sprintf_s_l、swprintf_s、_swprintf_s_l。](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)

以下代码演示了一些 Boost 格式设置功能。

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>另请参阅

[欢迎回到C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[C++语言参考](../cpp/cpp-language-reference.md)<br/>
[C++标准库](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<限制>](../standard-library/limits.md)<br/>
[\<奥马尼普>](../standard-library/iomanip.md)
