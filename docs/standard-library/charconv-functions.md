---
title: '&lt;charconv &gt; 函数'
ms.date: 07/22/2020
f1_keywords:
- charconv/std::to_chars
- charconv/std::from_chars
helpviewer_keywords:
- std::charconv [C++], to_chars
- std::charconv [C++], from_chars
ms.openlocfilehash: 276ac2bce70ce5c4ebf8e22bb1da1ac9914db55e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230195"
---
# <a name="ltcharconvgt-functions"></a>&lt;charconv &gt; 函数

\<charconv>标头包括下列非成员函数：

| **非成员函数** | **说明** |
|-|-|
|[to_chars](#to_chars) | 将整数或浮点值转换为的序列 **`char`** 。 |
|[from_chars](#from_chars) | 将的序列转换 **`char`** 为整数或浮点值。 |

这些转换函数针对性能进行了优化，并且还支持最短的往返行为。 最短往返行为意味着当数字转换为字符时，只写出足够的精度，以便在将这些字符转换回浮点时恢复原始数字。

- 将字符转换为数字时，数值不需要以 null 值结束。 同样，将数字转换为字符时，结果不是以 null 结尾的。
- 转换函数不分配内存。 所有情况下都拥有缓冲区。
- 转换函数不会引发。 返回一个结果，您可以从该结果确定转换是否成功。
- 转换函数不区分运行时舍入模式。
- 转换函数不是区域设置感知。 它们始终将小数点打印并分析为 `'.'` 使用逗号的区域设置，而不是使用 "，"。

## `to_chars`

将整数或浮点值转换为的序列 **`char`** 。

`value`通过填充范围来转换为字符串， \[ `first` `last` 其中 \[ `first` ， `last` ）必须为有效范围。
返回[to_chars_result 结构](to-chars-result-structure.md)。 如果转换成功，则为 `to_char_result.ec` ，成员 `ptr` 是所写入字符的一-后端指针。 否则， `to_char_result.ec` 具有值 `errc::value_too_large` ，其 `to_char_result.ptr` 值为， `last` 并且 \[ `first` 未指定范围的内容 `last` 。

`to_chars`如果您提供不足大的缓冲区来保存结果，则唯一可能会失败的方法是。

```cpp
// integer to chars

to_chars_result to_chars(char* first, char* last, char value, int base = 10);
to_chars_result to_chars(char* first, char* last, signed char value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned char value, int base = 10);
to_chars_result to_chars(char* first, char* last, short value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned short value, int base = 10);
to_chars_result to_chars(char* first, char* last, int value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned int value, int base = 10);
to_chars_result to_chars(char* first, char* last, long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long value, int base = 10);
to_chars_result to_chars(char* first, char* last, long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, unsigned long long value, int base = 10);
to_chars_result to_chars(char* first, char* last, bool value, int base = 10) = delete;

// floating-point to chars

to_chars_result to_chars(char* first, char* last, float value);
to_chars_result to_chars(char* first, char* last, double value);
to_chars_result to_chars(char* first, char* last, long double value);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt);
to_chars_result to_chars(char* first, char* last, float value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, double value, chars_format fmt, int precision);
to_chars_result to_chars(char* first, char* last, long double value, chars_format fmt, int precision);
```

### <a name="parameters"></a>参数

*1*\
指向要填充的缓冲区的开头。

*时间*\
指向要填充的缓冲区末尾的一个字符。

*负值*\
要转换的值。 如果 `value` 为负，则表示形式以开头 `-` 。

*基座*\
对于整数转换，是转换为字符时要使用的基 `value` 。 必须介于2和36（含）之间。 不会有前导零。 介于 10. 35 （含）之间的数字表示为小写字符 a.。z

*bcp.fmt*\
对于浮点转换，为用于指定要使用的转换格式（如科学、固定或十六进制）的位掩码。 有关详细信息，请参阅[chars_format](chars-format-class.md) 。

*precision*\
对于浮点转换，为转换后的值的精度位数。

### <a name="return-value"></a>返回值

包含转换结果的[to_chars_result](to-chars-result-structure.md) 。

### <a name="remarks"></a>备注

采用[chars_format](chars-format-class.md)参数的函数会确定转换说明符，就像它们使用如下所示：如果为，则为; 如果为，则为; 如果为，则为; 如果为，则为 `printf()` `f` `fmt` `chars_format::fixed` `e` `fmt` `chars_format::scientific` `a` `fmt` `chars_format::hex` `g` `fmt` `chars_format::general` 。 指定最短的固定表示法仍可能会导致长时间的输出，因为当值非常大或很小时，可能是最短的表示形式。

下表描述了和参数的不同组合的转换 `fmt` 行为 `precision` 。 "最短往返" 一词是指写入所需的最少位数，以便使用相应的函数分析该表示形式 `from_chars` 会完全恢复值。

| `fmt`and `precision` 组合 | 输出 |
|--|--|
|  两者均未选中 | 无论是固定的还是科学记数法，都要将其作为 tiebreaker 进行修复。</br>此行为不能由采用参数的任何重载模拟 `fmt` 。 |
| `fmt` | 指定格式的最短往返行为，如最短科学格式。 |
| `fmt` 和 `precision` | 使用以下样式的给定精度（ `printf()` 无最短往返行为）。 |

### <a name="return-value"></a>返回值

保存转换结果的[to_chars_result](to-chars-result-structure.md) 。

### <a name="example"></a>示例

```cpp
#include <charconv>
#include <stdio.h>
#include <system_error>

template <typename T> void TestToChars(const T t)
{
    static_assert(std::is_floating_point_v<T>);
    constexpr bool IsFloat = std::is_same_v<T, float>;

    char buf[100]; // 100 is large enough for double and long double values because the longest possible outputs are "-1.23456735e-36" and "-1.2345678901234567e-100".
    constexpr size_t size = IsFloat ? 15 : 24;
    const std::to_chars_result res = std::to_chars(buf, buf + size, t);  // points to buffer area it can use. Must be char, not wchar_t, etc.
    
    if (res.ec == std::errc{}) // no error
    {
        // %.*s provides the exact number of characters to output because the output range, [buf, res.ptr), isn't null-terminated
        printf("success: %.*s\n", static_cast<int>(res.ptr - buf), buf);
    }
    else // probably std::errc::value_too_large
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }
}

int main()
{
    TestToChars(123.34);
    return 0;
}
```

## `from_chars`

将的序列转换 **`char`** 为整数或浮点值。

```cpp
// char to an integer value

from_chars_result from_chars(const char* first, const char* last, char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, signed char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned char& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned short& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned int& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, long long& value, int base = 10);
from_chars_result from_chars(const char* first, const char* last, unsigned long long& value, int base = 10);

// char to a floating-point value

from_chars_result from_chars(const char* first, const char* last, float& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, double& value, chars_format fmt = chars_format::general);
from_chars_result from_chars(const char* first, const char* last, long double& value, chars_format fmt = chars_format::general);
```

### <a name="parameters"></a>参数

*1*\
指向要转换的字符缓冲区的开头。

*时间*\
指向要转换的字符的缓冲区结尾元素之后的一个。

*负值*\
如果转换成功，则包含转换的结果。

*基座*\
对于整数转换，是要在转换过程中使用的基。 必须介于2和36（含）之间。

*bcp.fmt*\
对于浮点转换，则为要转换的字符序列的格式。 有关详细信息，请参阅[chars_format](chars-format-class.md) 。

### <a name="remarks"></a>备注

`from_chars()`用于分析字符串的函数（ \[ `first` `last` 其中，）必须为 \[ `first` `last` 有效范围。

分析字符时，不忽略空格。 `strtod()`例如，缓冲区的开头必须是有效的数字表示形式。

返回[from_chars_result 结构](from-chars-result-structure.md)。

如果没有任何字符匹配数字模式， `value` 则未修改， `from_chars_result.ptr` 指向 `first` ，并 `from_chars_result.ec` 为 `errc::invalid_argument` 。

如果只有一些字符与数字模式匹配，则 `from_chars_result.ptr` 指向第一个不与模式匹配的字符， `last` 如果所有字符均匹配，则为参数的值。

如果分析的值不在的类型所表示的范围内 `value` ， `value` 则将不修改且 `from_chars_result.ec` 为 `errc::result_out_of_range` 。

否则， `value` 设置为分析后的值，并在舍入后 `from_chars_result.ec` 等于 `errc{}` 。

### <a name="example"></a>示例

```cpp
#include <charconv>
#include <stdio.h>
#include <string_view>
#include <system_error>

double TestFromChars(const std::string_view sv)
{
    const char* const first = sv.data();
    const char* const last = first + sv.size();
    double dbl;

    const std::from_chars_result res = std::from_chars(first, last, dbl);

    if (res.ec == std::errc{}) // no error
    {
        printf("success: %g\n", dbl);
    }
    else
    {
        printf("Error: %d\n", static_cast<int>(res.ec));
    }

    return dbl;
}

int main()
{
    double dbl = TestFromChars("123.34");
    return 0;
}
```

## <a name="see-also"></a>另请参阅

[\<charconv>](charconv.md)  
[往返的最短十进制字符串](https://www.exploringbinary.com/the-shortest-decimal-string-that-round-trips-examples/)