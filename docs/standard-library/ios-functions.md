---
title: '&lt;ios&gt; 函数'
ms.date: 11/04/2016
f1_keywords:
- xiosbase/std::defaultfloat
- xiosbase/std::boolalpha
- xiosbase/std::dec
- ios/std::fixed
- ios/std::hex
- ios/std::internal
- ios/std::left
- ios/std::noboolalpha
- ios/std::noshowbase
- ios/std::noshowpoint
- ios/std::noshowpos
- ios/std::noskipws
- ios/std::nounitbuf
- ios/std::nouppercase
- ios/std::oct
- ios/std::right
- ios/std::scientific
- ios/std::showbase
- ios/std::showpoint
- ios/std::showpos
- ios/std::skipws
- ios/std::unitbuf
- ios/std::uppercase
ms.assetid: 1382d53f-e531-4b41-adf6-6a1543512e51
helpviewer_keywords:
- std::defaultfloat [C++]
- std::boolalpha [C++]
- std::dec [C++]
- std::fixed [C++]
- std::hex [C++]
- std::hexfloat [C++]
- std::io_errc [C++]
- std::internal [C++]
- std::iostream_category [C++]
- std::is_error_code_enum [C++]
- std::left [C++]
- std::make_error_code [C++]
- std::make_error_condition [C++]
- std::noboolalpha [C++]
- std::noshowbase [C++]
- std::noshowpoint [C++]
- std::noshowpos [C++]
- std::noskipws [C++]
- std::nounitbuf [C++]
- std::nouppercase [C++]
- std::oct [C++]
- std::right [C++]
- std::scientific [C++]
- std::showbase [C++]
- std::showpoint [C++]
- std::showpos [C++]
- std::skipws [C++]
- std::unitbuf [C++]
- std::uppercase [C++]
ms.openlocfilehash: 67ac9259110abbd03fc054ea4e60ed1715030dcc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375414"
---
# <a name="ltiosgt-functions"></a>&lt;ios&gt; 函数

## <a name="boolalpha"></a><a name="boolalpha"></a>布尔阿尔法

指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 **true** 或 **false**。

```cpp
ios_base& boolalpha(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

默认情况下，**布尔**类型的变量显示为 1 或 0。

`boolalpha`有效地调用`str.` [setf](../standard-library/ios-base-class.md#setf)（），`ios_base::boolalpha`然后返回*str*。

[noboolalpha](../standard-library/ios-functions.md#noboolalpha) 会取消 `boolalpha` 的效果。

### <a name="example"></a>示例

```cpp
// ios_boolalpha.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   bool b = true;
   cout << b << endl;
   boolalpha( cout );
   cout << b << endl;
   noboolalpha( cout );
   cout << b << endl;
   cout << boolalpha << b << endl;
}
```

```Output
1
true
1
true
```

## <a name="dec"></a><a name="dec"></a>12 月

指定以十进制计数法形式显示整数变量。

```cpp
ios_base& dec(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

默认情况下，整型变量以十进制计数法显示。

`dec`有效地调用`str.` [setf](../standard-library/ios-base-class.md#setf) `ios_base::basefield`（，），`ios_base::dec`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_dec.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 100;

   cout << i << endl;   // Default is base 10
   cout << hex << i << endl;
   dec( cout );
   cout << i << endl;
   oct( cout );
   cout << i << endl;
   cout << dec << i << endl;
}
```

```Output
100
64
100
144
100
```

## <a name="ltiosgt-defaultfloat"></a><a name="ios_defaultfloat"></a> &lt;ios&gt; defaultfloat

配置 `ios_base` 对象的标记以使用浮点值的默认显示格式。

```cpp
ios_base& defaultfloat(ios_base& iosbase);
```

### <a name="parameters"></a>参数

*_Iosbase*\
一个 `ios_base` 对象。

### <a name="remarks"></a>备注

操纵器有效地调用`iosbase.`[ios_base：unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::floatfield)`然后返回*iosbase。*

## <a name="fixed"></a><a name="fixed"></a>固定

指定浮点数以自动设置小数点表示法显示。

```cpp
ios_base& fixed(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

`fixed`是浮点数字的默认显示表示法。 [scientific](../standard-library/ios-functions.md#scientific) 会导致使用科学记数法显示浮点数。

操纵器有效地调用*str*。[setf](../standard-library/ios-base-class.md#setf) `ios_base::fixed`（，`ios_base::floatfield`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_fixed.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 1.1F;

   cout << i << endl;   // fixed is the default
   cout << scientific << i << endl;
   cout.precision( 1 );
   cout << fixed << i << endl;
}
```

```Output
1.1
1.100000e+000
1.1
```

## <a name="hex"></a><a name="hex"></a>十六进制

指定以十六进制计数法形式显示整型变量。

```cpp
ios_base& hex(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

默认情况下，整型变量以十进制计数法显示。 [dec](../standard-library/ios-functions.md#dec) 和 [oct](../standard-library/ios-functions.md#oct) 也会改变整型变量显示的方式。

操纵器有效地调用`str` **。**[setf](../standard-library/ios-base-class.md#setf) `ios_base::hex`（，`ios_base::basefield`然后返回*str*。

### <a name="example"></a>示例

有关如何使用`hex`的示例，请参阅[dec。](../standard-library/ios-functions.md#dec)

## <a name="hexfloat"></a><a name="hexfloat"></a>六角漂浮

```cpp
ios_base& hexfloat (ios_base& str);
```

## <a name="io_errc"></a><a name="io_errc"></a>io_errc

```cpp
enum class io_errc {
    stream = 1
};
```

## <a name="internal"></a><a name="internal"></a>内部

导致数字的符号左对齐，数字右对齐。

```cpp
ios_base& internal(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

[showpos](../standard-library/ios-functions.md#showpos) 会对正数显示此符号。

操纵器有效地调用`str.` [setf](../standard-library/ios-base-class.md#setf)`(`[ios_base：内部](../standard-library/ios-base-class.md#fmtflags)`,`[ios_base：调整场](../standard-library/ios-base-class.md#fmtflags)`)`，然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_internal.cpp
// compile with: /EHsc
#include <iostream>
#include <iomanip>

int main( void )
{
   using namespace std;
   float i = -123.456F;
   cout.fill( '.' );
   cout << setw( 10 ) << i << endl;
   cout << setw( 10 ) << internal << i << endl;
}
```

```Output
..-123.456
-..123.456
```

## <a name="is_error_code_enum"></a><a name="is_error_code_enum"></a>is_error_code_enum

```cpp
template <> struct is_error_code_enum<io_errc> : public true_type { };
```

## <a name="iostream_category"></a><a name="iostream_category"></a>iostream_category

```cpp
const error_category& iostream_category() noexcept;
```

## <a name="left"></a><a name="left"></a>离开

导致宽度比输出宽度短的文本在流刷新过程中显示时带有左边距。

```cpp
ios_base& left(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::left, ios_base::adjustfield)`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_left.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout.width( 20 );
   cout << f1 << endl;
   cout << left << f1 << endl;
}
```

```Output
5
        5
```

## <a name="make_error_code"></a><a name="make_error_code"></a>make_error_code

```cpp
error_code make_error_code(io_errc e) noexcept;
```

## <a name="make_error_condition"></a><a name="make_error_condition"></a>make_error_condition

```cpp
error_condition make_error_condition(io_errc e) noexcept;
```

## <a name="noboolalpha"></a><a name="noboolalpha"></a>诺布尔阿尔法

指定类型为 [bool](../cpp/bool-cpp.md) 的变量在流中显示为 1 或 0。

```cpp
ios_base& noboolalpha(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

默认情况，`noboolalpha` 是有效的。

`noboolalpha`有效地调用`str.` [unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::boolalpha)`然后返回*str*。

[boolalpha](../standard-library/ios-functions.md#boolalpha) 会取消 `noboolalpha` 的效果。

### <a name="example"></a>示例

有关使用 `noboolalpha` 的示例，请参阅 [boolalpha](../standard-library/ios-functions.md#boolalpha)。

## <a name="noshowbase"></a><a name="noshowbase"></a>无显示基地

关闭显示数字所采用的进制的指示。

```cpp
ios_base& noshowbase(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

`noshowbase` 处于打开状态。 使用 [showbase](../standard-library/ios-functions.md#showbase) 来指示数字基数。

`str.`操纵器有效地调用[unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::showbase)`然后返回*str*。

### <a name="example"></a>示例

有关如何使用 `noshowbase` 的示例，请参阅 [showbase](../standard-library/ios-functions.md#showbase)。

## <a name="noshowpoint"></a><a name="noshowpoint"></a>无显示点

仅显示浮点数（其小数部分为零）的整数部分。

```cpp
ios_base& noshowpoint(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

`noshowpoint` 默认为打开；使用 [showpoint](../standard-library/ios-functions.md#showpoint) 和 [precision](../standard-library/ios-base-class.md#precision) 显示小数点后的零。

`str.`操纵器有效地调用[unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::showpoint)`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_noshowpoint.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.000;
   cout << f1 << endl;   // noshowpoint is default
   cout.precision( 4 );
   cout << showpoint << f1 << endl;
   cout << noshowpoint << f1 << endl;
}
```

```Output
5
5.000
5
```

## <a name="noshowpos"></a><a name="noshowpos"></a>诺秀波

导致正数不显式带有符号。

```cpp
ios_base& noshowpos(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

`noshowpos` 处于打开状态。

`str.`操纵器有效地调用[unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::showps)`然后返回*str*。

### <a name="example"></a>示例

有关使用 `noshowpos` 的示例，请参阅 [showpos](../standard-library/ios-functions.md#showpos)。

## <a name="noskipws"></a><a name="noskipws"></a>诺斯基普斯

导致输入流读取空格。

```cpp
ios_base& noskipws(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

[skipws](../standard-library/ios-functions.md#skipws) 默认为开启状态。 读取到流中的空格时，它表示缓冲区的结束。

`str.`操纵器有效地调用[unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::skipws)`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_noskipws.cpp
// compile with: /EHsc
#include <iostream>
#include <string>

int main() {
   using namespace std;
   string s1, s2, s3;
   cout << "Enter three strings: ";
   cin >> noskipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

## <a name="nounitbuf"></a><a name="nounitbuf"></a>努尼布夫

导致缓冲区已满时缓冲和处理输出。

```cpp
ios_base& nounitbuf(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

[unitbuf](../standard-library/ios-functions.md#unitbuf) 导致在缓冲区未满时处理缓冲区。

`str.`操纵器有效地调用[unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::unitbuf)`然后返回*str*。

## <a name="nouppercase"></a><a name="nouppercase"></a>无大写

指定十六进制数字和科学计数法形式的指数以小写形式显示。

```cpp
ios_base& nouppercase(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

`str.`操纵器有效地调用[unsetf，](../standard-library/ios-base-class.md#unsetf)`(ios_base::uppercase)`然后返回*str*。

### <a name="example"></a>示例

有关使用 `nouppercase` 的示例，请参阅 [uppercase](../standard-library/ios-functions.md#uppercase)。

## <a name="oct"></a><a name="oct"></a>十月

指定以八进制计数法形式显示整数变量。

```cpp
ios_base& oct(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

默认情况下，整型变量以十进制计数法显示。 [dec](../standard-library/ios-functions.md#dec) 和 [hex](../standard-library/ios-functions.md#hex) 也会改变整型变量显示的方式。

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::oct, ios_base::basefield)`然后返回*str*。

### <a name="example"></a>示例

有关如何使用`oct`的示例，请参阅[dec。](../standard-library/ios-functions.md#dec)

## <a name="right"></a><a name="right"></a>对

导致宽度比输出宽度短的文本在流刷新过程中显示时带有右边距。

```cpp
ios_base& right(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

[left](../standard-library/ios-functions.md#left) 还会修改文本对齐方式。

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::right, ios_base::adjustfield)`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_right.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   double f1= 5.00;
   cout << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << left << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
   cout.width( 20 );
   cout << right << f1 << endl;
   cout.width( 20 );
   cout << f1 << endl;
}
```

```Output
5
                   5
5
5
                   5
                   5
```

## <a name="scientific"></a><a name="scientific"></a>科学

导致使用科学记数法显示浮点数。

```cpp
ios_base& scientific(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

默认对浮点数启用 [fixed](../standard-library/ios-functions.md#fixed) 表示法。

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::scientific, ios_base::floatfield)`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_scientific.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   float i = 100.23F;

   cout << i << endl;
   cout << scientific << i << endl;
}
```

```Output
100.23
1.002300e+002
```

## <a name="showbase"></a><a name="showbase"></a>显示库

指示显示数字所采用的进制。

```cpp
ios_base& showbase(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

可使用 [dec](../standard-library/ios-functions.md#dec)、[oct](../standard-library/ios-functions.md#oct) 或 [hex](../standard-library/ios-functions.md#hex) 更改数字的基数。

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::showbase)`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_showbase.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int j = 100;

   cout << showbase << j << endl;   // dec is default
   cout << hex << j << showbase << endl;
   cout << oct << j << showbase << endl;

   cout << dec << j << noshowbase << endl;
   cout << hex << j << noshowbase << endl;
   cout << oct << j << noshowbase << endl;
}
```

```Output
100
0x64
0144
100
64
144
```

## <a name="showpoint"></a><a name="showpoint"></a>显示点

显示浮点数的整数部分和小数点右侧的数字，即使小数部分为零。

```cpp
ios_base& showpoint(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

[noshowpoint](../standard-library/ios-functions.md#noshowpoint) 默认为开启状态。

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::showpoint)`然后返回*str*。

### <a name="example"></a>示例

有关使用 `showpoint` 的示例，请参阅 [noshowpoint](../standard-library/ios-functions.md#noshowpoint)。

## <a name="showpos"></a><a name="showpos"></a>显示波

导致正数显式带有符号。

```cpp
ios_base& showpos(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

[noshowpos](../standard-library/ios-functions.md#noshowpos) 为默认值。

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::showpos)`然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_showpos.cpp
// compile with: /EHsc
#include <iostream>

int main( )
{
   using namespace std;
   int i = 1;

   cout << noshowpos << i << endl;   // noshowpos is default
   cout << showpos << i << endl;
}
```

```Output
1
+1
```

## <a name="skipws"></a><a name="skipws"></a>跳过

导致输入流不读取空格。

```cpp
ios_base& skipws(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

默认情况，`skipws` 是有效的。 [noskipws](../standard-library/ios-functions.md#noskipws) 会导致从输入流中读取空格。

`str.`操纵器有效地调用[setf，](../standard-library/ios-base-class.md#setf)`(ios_base::skipws)`然后返回*str*。

### <a name="example"></a>示例

```cpp
#include <iostream>
#include <string>

int main( )
{
   using namespace std;
   char s1, s2, s3;
   cout << "Enter three characters: ";
   cin >> skipws >> s1 >> s2 >> s3;
   cout << "." << s1  << "." << endl;
   cout << "." << s2 << "." << endl;
   cout << "." << s3 << "." << endl;
}
```

```Input
1 2 3
```

```Output
Enter three characters: 1 2 3
.1.
.2.
.3.
```

## <a name="unitbuf"></a><a name="unitbuf"></a>单位布夫

导致在缓冲区未满时处理输出。

```cpp
ios_base& unitbuf(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

请注意，`endl` 也会刷新缓冲区。

[nounitbuf](../standard-library/ios-functions.md#nounitbuf) 默认为开启状态。

操纵`str.`器有效地调用[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base：单位buf，](../standard-library/ios-base-class.md#fmtflags)`)`然后返回*str*。

## <a name="uppercase"></a><a name="uppercase"></a>大写

指定十六进制数字和科学计数法形式的指数以大写形式显示。

```cpp
ios_base& uppercase(ios_base& str);
```

### <a name="parameters"></a>参数

*Str*\
对 [ios_base](../standard-library/ios-base-class.md) 类型的对象的引用，或对从 `ios_base` 继承的类型的引用。

### <a name="return-value"></a>返回值

对派生*str*的对象的引用。

### <a name="remarks"></a>备注

[nouppercase](../standard-library/ios-functions.md#nouppercase) 默认为开启状态。

操纵`str.`器有效地调用[setf](../standard-library/ios-base-class.md#setf)`(`[ios_base：大写](../standard-library/ios-base-class.md#fmtflags)`)`，然后返回*str*。

### <a name="example"></a>示例

```cpp
// ios_uppercase.cpp
// compile with: /EHsc
#include <iostream>

int main( void )
{
   using namespace std;

   double i = 1.23e100;
   cout << i << endl;
   cout << uppercase << i << endl;

   int j = 10;
   cout << hex << nouppercase << j << endl;
   cout << hex << uppercase << j << endl;
}
```

```Output
1.23e+100
1.23E+100
a
A
```
