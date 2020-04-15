---
title: Platform::String 类
ms.date: 10/16/2019
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::String::String
- VCCORLIB/Platform::String::Begin
- VCCORLIB/Platform::String::CompareOrdinal
- VCCORLIB/Platform::String::Concat
- VCCORLIB/Platform::String::Data
- VCCORLIB/Platform::String::Dispose
- VCCORLIB/Platform::String::End
- VCCORLIB/Platform::String::Equals
- VCCORLIB/Platform::String::GetHashCode
- VCCORLIB/Platform::String::IsEmpty
- VCCORLIB/Platform::String::IsFastPass
- VCCORLIB/Platform::String::Length
- VCCORLIB/Platform::String::ToString
helpviewer_keywords:
- Platform::String
ms.assetid: 72dd04a4-a694-40d3-b899-eaa0b503eab8
ms.openlocfilehash: 3f29c60d0d6a4618d97d8f750a048fcc18f976b5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322116"
---
# <a name="platformstring-class"></a>Platform::String 类

用于表示文本的 Unicode 字符的有序集合。 有关详细信息和示例，请参阅[字符串](../cppcx/strings-c-cx.md)。

## <a name="syntax"></a>语法

```cpp
public ref class String sealed : Object,
    IDisposable,
    IEquatable,
    IPrintable
```

## <a name="iterators"></a>迭代器

两个迭代器函数（不是字符串类的成员）可以和 `std::for_each` 模板函数合用来枚举字符串对象中的字符。

|成员|说明|
|------------|-----------------|
|`const char16* begin(String^ s)`|返回指向指定字符串对象开头的指针。|
|`const char16* end(String^ s)`|返回通过指定字符串对象末尾的指针。|

## <a name="members"></a>成员

此字符串类从对象、IDisposable、IEquatable 和 IPrintable 接口继承。

此字符串类还具有以下类型的成员。

### <a name="constructors"></a>构造函数

|成员|说明|
|------------|-----------------|
|[字符串：字符串](#ctor)|初始化字符串类的新实例。|

### <a name="methods"></a>方法

此字符串类从 [Platform::Object Class](../cppcx/platform-object-class.md)继承 Equals()、Finalize(), GetHashCode()、GetType()、MemberwiseClose() 和 ToString() 方法。 字符串还具有以下方法。

|方法|说明|
|------------|-----------------|
|[字符串：：开始](#begin)|返回指向当前字符串开头的指针。|
|[字符串：：比较Ordinal](#compareordinal)|通过估计对象所表示的两个字符值中相应字符的数字值来比较两个 `String` 对象。|
|[字符串：：康卡特](#concat)|连接两个字符串对象的值。|
|[字符串：:D](#data)|返回指向当前字符串开头的指针。|
|[字符串：:D](#dispose)|释放资源。|
|[字符串：结束](#end)|返回通过当前字符串末尾的指针。|
|[字符串：等于](#equals)|指示指定对象是否等于当前对象。|
|[字符串：：获取哈希码](#gethashcode)|返回此实例的哈希代码。|
|[字符串：：为空](#isempty)|指示当前字符串对象是否为空。|
|[字符串：：IsFastPass](#isfastpass)|指示当前 String 对象是否参与*快速传递*操作。 在快速传递操作中，将挂起引用计数。|
|[字符串：长度](#length)|检索当前字符串对象的长度。|
|[字符串：：到字符串](#tostring)|返回一个字符串对象，其值与当前字符串相同。|

### <a name="operators"></a>运算符

String 类具有以下运算符。

|成员|说明|
|------------|-----------------|
|[字符串：：运算符 = 运算符](#operator-equality)|指示两个指定的 String 对象是否具有相同的值。|
|[operator+ 运算符](#operator-plus)|将两个字符串对象串联成一个新的字符串对象。|
|[字符串：：运算符>运算符](#operator-greater-than)|指示一个字符串对象的值是否大于或等于第二个字符串对象的值。|
|[字符串：：运算符>= 运算符](#operator-greater-than-or-equals)|指示一个字符串对象的值是否大于或等于第二个字符串对象的值。|
|[字符串：：运算符！= 运算符](#operator-inequality)|指示两个指定的 String 对象是否具有不同的值。|
|[字符串：：运算符<运算符](#operator-less-than)|指示一个字符串对象的值是否小于第二个字符串对象的值。|

### <a name="requirements"></a>要求

**受支持的最小客户端：** 视窗 8

**受支持的服务器最少：** 视窗服务器 2012

**命名空间：** Platform

**头文件** vccorlib.h（默认包含在内）

## <a name="stringbegin-method"></a><a name="begin"></a>字符串：：开始方法

返回指向当前字符串开头的指针。

### <a name="syntax"></a>语法

```cpp
char16* Begin();
```

### <a name="return-value"></a>返回值

指向当前字符串开头的指针。

## <a name="stringcompareordinal-method"></a><a name="compareordinal"></a>字符串：：比较元法

静态方法，通过计算`String`对象表示的两个字符串值中相应字符的数值来比较两个对象。

### <a name="syntax"></a>语法

```cpp
static int CompareOrdinal( String^ str1, String^ str2 );
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串对象。

*str2*<br/>
第二个字符串对象。

### <a name="return-value"></a>返回值

一个整数，指示两个比较字之间的词法关系。 下表列出可能的返回值。

|“值”|条件|
|-----------|---------------|
|-1|`str1` 小于 `str2`。|
|0|`str1` 等于 `str2`。|
|1|`str1` 大于 `str2`。|

## <a name="stringconcat-method"></a><a name="concat"></a>字符串：：Concat 方法

连接两个字符串对象的值。

### <a name="syntax"></a>语法

```cpp
String^ Concat( String^ str1, String^ str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个字符串对象或 `null`。

*str2*<br/>
第二个字符串对象或 `null`。

### <a name="return-value"></a>返回值

其值为 `str1` 与 `str2` 的值相连的新 String^ 对象。

如果 `str1` 是 `null` 而 `str2` 不是，则返回 `str1`。 如果 `str2` 是 `null` 而 `str1` 不是，则返回 `str2`。 如果 `str1` 和 `str2` 都是 `null`，则返回空字符串 (L "")。

## <a name="stringdata-method"></a><a name="data"></a>字符串：:Data 方法

以 C 样式 `char16` (`wchar_t`) 元素数组的形式返回指向对象的数据缓冲区开头的指针。

### <a name="syntax"></a>语法

```cpp
const char16* Data();
```

### <a name="return-value"></a>返回值

指向 Unicode 字符`const char16`数组开头的指针（`char16`是`wchar_t`类型的 def。

### <a name="remarks"></a>备注

使用此方法可从 `Platform::String^` 转换为 `wchar_t*`。 当 `String` 对象超出范围时，数据指针不再保证有效。 要将数据存储在原始`String`对象的生存期之外，请使用[wcscpy_s](../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md)将数组复制到自己分配的内存中。

## <a name="stringdispose-method"></a><a name="dispose"></a>字符串：:D分法

释放资源。

### <a name="syntax"></a>语法

```cpp
virtual override void Dispose();
```

## <a name="stringend-method"></a><a name="end"></a>字符串：：结束方法

返回通过当前字符串末尾的指针。

### <a name="syntax"></a>语法

```cpp
char16* End();
```

### <a name="return-value"></a>返回值

指向超出当前字符串末尾的指针。

### <a name="remarks"></a>备注

结束（） 返回开始（） = 长度。

## <a name="stringequals-method"></a><a name="equals"></a>字符串：：等于方法

指示指定的字符串是否具有和当前对象相同的值。

### <a name="syntax"></a>语法

```cpp
bool String::Equals(Object^ str);
bool String::Equals(String^ str);
```

### <a name="parameters"></a>参数

*Str*<br/>
要比较的对象。

### <a name="return-value"></a>返回值

如果等于当前对象，**则为 true;** `str`否则，**假**。

### <a name="remarks"></a>备注

此方法等效于静态[字符串：：比较Ordinal](#compareordinal)。 在第一个重载中，`str` 参数应能够转换为 String^ 对象。

## <a name="stringgethashcode-method"></a><a name="gethashcode"></a>字符串：：获取哈希码方法

返回此实例的哈希代码。

### <a name="syntax"></a>语法

```cpp
virtual override int GetHashCode();
```

### <a name="return-value"></a>返回值

此实例的哈希代码。

## <a name="stringisempty-method"></a><a name="isempty"></a>字符串：：为空方法

指示当前字符串对象是否为空。

### <a name="syntax"></a>语法

```cpp
bool IsEmpty();
```

### <a name="return-value"></a>返回值

如果当前`String`对象**为空**或空字符串 （L""），**则为 true;** 否则，**假**。

## <a name="stringisfastpass-method"></a><a name="isfastpass"></a>字符串：：isFastPass 方法

指示当前 String 对象是否参与*快速传递*操作。 在快速传递操作中，将挂起引用计数。

### <a name="syntax"></a>语法

```cpp
bool IsFastPass();
```

### <a name="return-value"></a>返回值

如果当前`String`对象是快速过去，**则为 true;** 否则，**假**。

### <a name="remarks"></a>备注

在引用计数对象作为参数并且被调用的函数只读取该对象的函数调用中，编译器可以安全地挂起引用计数并改进调用性能。 没有可供你的代码对此属性执行的任何操作。 系统处理所有详细信息。

## <a name="stringlength-method"></a><a name="length"></a>字符串：长度方法

检索当前`String`对象中的字符数。

### <a name="syntax"></a>语法

```cpp
unsigned int Length();
```

### <a name="return-value"></a>返回值

当前`String`对象中的字符数。

### <a name="remarks"></a>备注

一个没有字符的字符串的长度为零。 以下字符串的长度为 5：

```cpp
String^ str = "Hello";
int len = str->Length(); //len = 5
```

[String：:Data](#data)返回的字符数组具有一个附加字符，即终止 NULL 或"\0"。 该字符也是两个字节长。

## <a name="stringoperator-operator"></a><a name="operator-plus"></a>字符串：：运算符+ 运算符

将两个[字符串](../cppcx/platform-string-class.md)对象合并到新的[String](../cppcx/platform-string-class.md)对象中。

### <a name="syntax"></a>语法

```cpp
bool String::operator+( String^ str1, String^ str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个 `String` 对象。

*str2*<br/>
第二个 `String` 对象，其内容将追加到 `str1`。

### <a name="return-value"></a>返回值

如果*str1*等于*str2，***则为 true;** 否则，**假**。

### <a name="remarks"></a>备注

此运算符创建一个 `String^` 对象，用以包含两个操作数中的数据。 在极端性能并不重要时，使用它只是为了方便。 函数中有些对“`+`”的调用可能不明显，但如果在紧凑循环中操作大对象或文本数据，则使用标准 C++ 机制和类型。

## <a name="stringoperator-operator"></a><a name="operator-equality"></a>字符串：：运算符 = 运算符

指示指定的字符串对象是否具有相同的文本值。

### <a name="syntax"></a>语法

```cpp
bool String::operator==( String^ str1, String^ str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
要比较的第一个 `String` 对象。

*str2*<br/>
要比较的第二个 `String` 对象。

### <a name="return-value"></a>返回值

**如果**的内容`str1`等于`str2`;否则，**假**。

### <a name="remarks"></a>备注

此运算符等效于[String：：比较 Ordinal](#compareordinal)。

## <a name="stringoperatorgt"></a><a name="operator-greater-than"></a>字符串：：运算符&gt;

指示一个`String`对象的值是否大于第二`String`个对象的值。

### <a name="syntax"></a>语法

```cpp
bool String::operator>( String^ str1, String^ str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个 `String` 对象。

*str2*<br/>
第二个 `String` 对象。

### <a name="return-value"></a>返回值

**如果**的值`str1`大于`str2`的值 ，则 为 true。否则，**假**。

### <a name="remarks"></a>备注

此运算符等效于显式调用[String：：比较 Ordinal](#compareordinal)并获取大于零的结果。

## <a name="stringoperatorgt"></a><a name="operator-greater-than-or-equals"></a>字符串：：运算符&gt;=

指示一个`String`对象的值是否大于或等于第二`String`个对象的值。

### <a name="syntax"></a>语法

```cpp
bool String::operator>=( String^ str1, String^ str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个 `String` 对象。

*str2*<br/>
第二个 `String` 对象。

### <a name="return-value"></a>返回值

**如果**的值`str1`大于 或等于`str2`否则，**假**。

## <a name="stringoperator"></a><a name="operator-inequality"></a>字符串：：操作员！*

指示两个指定`String`对象是否具有不同的值。

### <a name="syntax"></a>语法

```cpp
bool String::operator!=( String^ str1, String^ str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
要比较的第一个 `String` 对象。

*str2*<br/>
要比较的第二个 `String` 对象。

### <a name="return-value"></a>返回值

如果不等于`str2`**，则为 true。** `str1`否则，**假**。

## <a name="stringoperatorlt"></a><a name="operator-less-than"></a>字符串：：运算符&lt;

指示一个`String`对象的值是否小于第二`String`个对象的值。

### <a name="syntax"></a>语法

```cpp
bool String::operator<( String^ str1, String^ str2);
```

### <a name="parameters"></a>参数

*str1*<br/>
第一个 `String` 对象。

*str2*<br/>
第二个 `String` 对象。

### <a name="return-value"></a>返回值

如果*str1*的值小于*str2*的值，**则为 true;** 否则，**假**。

## <a name="stringstring-constructor"></a><a name="ctor"></a>字符串：：字符串构造函数

使用输入字符串数据的副本初始化`String`类的新实例。

### <a name="syntax"></a>语法

```cpp
String();
String(char16* s);
String(char16* s, unsigned int n);
```

### <a name="parameters"></a>参数

*s*<br/>
初始化字符串的一系列宽字符。 char16

*n*<br/>
指定字符串长度的一个数字。

### <a name="remarks"></a>备注

如果性能至关重要，并且控制源字符串的生存期，则可以使用[Platform：stringReference](../cppcx/platform-stringreference-class.md)代替字符串。

### <a name="example"></a>示例

```cpp
String^ s = L"Hello!";
```

## <a name="stringtostring"></a><a name="tostring"></a>字符串：：到字符串

返回其`String`值与当前字符串相同的对象。

### <a name="syntax"></a>语法

```cpp
String^ String::ToString();
```

### <a name="return-value"></a>返回值

其`String`值与当前字符串相同的对象。

## <a name="see-also"></a>另请参阅

[Platform 命名空间](../cppcx/platform-namespace-c-cx.md)
