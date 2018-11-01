---
title: path 类
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 486245df3433f552c289786a0b20deb33c8fb6c0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618213"
---
# <a name="path-class"></a>path 类

**路径**类存储类型的对象`string_type`称为`myname`此处出于阐述，适合用作路径名称。 `string_type` 是的同义词`basic_string<value_type>`，其中`value_type`是的同义词**wchar_t**上 Windows 或**char** POSIX 上。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>语法

```cpp
class path;
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[path](#path)|构造一个 `path`。|

### <a name="typedefs"></a>Typedef

|类型名称|描述|
|-|-|
|[const_iterator](#const_iterator)|`iterator` 的同义词。|
|[Iterator](#iterator)|双向常量迭代器，指定`path`组件的`myname`。|
|[string_type](#string_type)|该类型是 `basic_string<value_type>` 的同义词。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[append](#append)|将追加到指定的序列`mypath`、 转换和根据需要插入 preferred_separator。|
|[assign](#assign)|替换`mypath`与指定序列中，按需转换。|
|[begin](#begin)|返回`path::iterator`指定路径名中的第一个路径元素，如果存在。|
|[c_str](#c_str)|将指针返回到的第一个字符`mypath`。|
|[clear](#clear)|执行`mypath.clear()`。|
|[compare](#compare)|返回比较值。|
|[concat](#compare)|将追加到指定的序列`mypath`、 转换 （但不是插入分隔符） 根据需要。|
|[empty](#empty)|返回 `mypath.empty()`。|
|[end](#end)|返回类型的序列末迭代器`iterator`。|
|[扩展](#extension)|返回的后缀`filename()`。|
|[filename](#filename)|返回 myname 的根目录组件，尤其是 `empty() path() : *--end()`。 组件可能为空。|
|[generic_string](#generic_string)|返回 `this->string<Elem, Traits, Alloc>(al)` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。|
|[generic_u16string](#generic_u16string)|返回 `u16string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。|
|[generic_u32string](#generic_u32string)|返回 `u32string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。|
|[generic_u8string](#generic_u8string)|返回 `u8string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。|
|[generic_wstring](#generic_wstring)|返回 `wstring()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。|
|[has_extension](#has_extension)|返回 `!extension().empty()`。|
|[has_filename](#has_filename)|返回 `!filename().empty()`。|
|[has_parent_path](#has_parent_path)|返回 `!parent_path().empty()`。|
|[has_relative_path](#has_relative_path)|返回 `!relative_path().empty()`。|
|[has_root_directory](#has_root_directory)|返回 `!root_directory().empty()`。|
|[has_root_name](#has_root_name)|返回 `!root_name().empty()`。|
|[has_root_path](#has_root_path)|返回 `!root_path().empty()`。|
|[has_stem](#has_stem)|返回 `!stem().empty()`。|
|[is_absolute](#is_absolute)|对于 Windows，函数返回`has_root_name() && has_root_directory()`。 对于 Posix，函数将返回`has_root_directory()`。|
|[is_relative](#is_relative)|返回 `!is_absolute()`。|
|[make_preferred](#make_preferred)|根据需要请将每个分隔符转换为 preferred_separator。|
|[本机](#native)|返回 `myname`。|
|[parent_path](#parent_path)|返回父路径组件`myname`。|
|[preferred_separator](#preferred_separator)|常量对象提供首选字符来分隔路径组件，具体取决于主机操作系统。 |
|[relative_path](#relative_path)|返回的相对路径组件`myname`。 |
|[remove_filename](#remove_filename)|删除文件名。|
|[replace_extension](#replace_extension)|替换的扩展`myname`。 |
|[replace_filename](#replace_filename)|RReplaces 文件名。|
|[root_directory](#root_directory)|返回的根组件`myname`。 |
|[root_name](#root_name)|返回的根名称组件`myname`。 |
|[root_path](#root_path)|返回的根路径组件`myname`。|
|[stem](#stem)|返回`stem`组件的`myname`。|
|[string](#string)|将转换中存储的序列`mypath`。|
|[swap](#swap)|执行`swap(mypath, right.mypath)`。|
|[u16string](#u16string)|将转换中存储的序列`mypath`utf-16 和存储中的类型的对象返回到`u16string`。|
|[u32string](#u32string)|将转换中存储的序列`mypath`UTF-32，它存储在类型的对象返回到`u32string`。|
|[u8string](#u8string)|将转换中存储的序列`mypath`utf-8，它存储在类型的对象返回到`u8string`。|
|[value_type](#value_type)|类型描述了主机操作系统偏好的路径元素。|
|[wstring](#wstring)|将转换中存储的序列`mypath`到为主机系统偏好的编码`wchar_t`序列，并返回它存储在类型的对象`wstring`。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_as)|将路径的元素替换为另一个路径的副本。|
|[operator+=](#op_add)|各种`concat`表达式。|
|[operator/=](#op_divide)|各种`append`表达式。|
|[string_type 运算符](#op_string)|返回 `myname`。|

## <a name="requirements"></a>要求

**标头：** \<文件系统 >

**命名空间：** std::experimental::filesystem

## <a name="append"></a> path:: append

将追加到指定的序列`mypath`、 转换和插入`preferred_separator`根据需要。

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*source*<br/>
指定的序列。

*first*<br/>
指定序列的开头。

*最后一个*<br/>
指定序列的末尾。

## <a name="assign"></a> path:: assign

替换`mypath`与指定序列中，按需转换。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*source*<br/>
指定的序列。

*first*<br/>
指定序列的开头。

*最后一个*<br/>
指定序列的末尾。

## <a name="begin"></a> path:: begin

返回`path::iterator`指定路径名中的第一个路径元素，如果存在。

```cpp
iterator begin() const;
```

## <a name="c_str"></a> path::c_str

将指针返回到的第一个字符`mypath`。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a> path:: clear

执行`mypath.clear()`。

```cpp
void clear() noexcept;
```

## <a name="compare"></a> path:: compare

第一个函数返回 `mypath.compare(pval.native())`。 第二个函数返回 `mypath.compare(str)`。 第三个函数返回`mypath.compare(ptr)`。

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>参数

*pval*<br/>
要比较的路径。

*str*<br/>
要比较的字符串。

*ptr*<br/>
要比较的指针。

## <a name="concat"></a> path:: concat

将追加到指定的序列`mypath`、 转换 （但不是插入分隔符） 根据需要。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*source*<br/>
指定的序列。

*first*<br/>
指定序列的开头。

*最后一个*<br/>
指定序列的末尾。

## <a name="const_iterator"></a> path::const_iterator

`iterator` 的同义词。

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a> path:: empty

返回 `mypath.empty()`。

```cpp
bool empty() const noexcept;
```

## <a name="end"></a> path:: end

返回类型的序列末迭代器`iterator`。

```cpp
iterator end() const;
```

## <a name="extension"></a> path:: extension

返回的后缀`filename()`。

```cpp
path extension() const;
```

### <a name="remarks"></a>备注

返回的后缀`filename() X`以便：

如果`X == path(".") || X == path("..")`或者，如果`X`不包含任何点，则前缀为空。

否则，前缀以最右侧的点开头（并将其包含在内）。

## <a name="filename"></a> path:: filename

返回 myname 的根目录组件，尤其是 `empty() path() : *--end()`。 组件可能为空。

```cpp
path filename() const;
```

## <a name="generic_string"></a> path::generic_string

返回 `this->string<Elem, Traits, Alloc>(al)` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a> path::generic_u16string

返回 `u16string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a> path::generic_u32string

返回 `u32string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a> path::generic_u8string

返回 `u8string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a> path::generic_wstring

返回 `wstring()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a> path::has_extension

返回 `!extension().empty()`。

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a> path:: has_filename

返回 `!filename().empty()`。

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a> path:: has_parent_path

返回 `!parent_path().empty()`。

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a> path:: has_relative_path

返回 `!relative_path().empty()`。

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a> path:: has_root_directory

返回 `!root_directory().empty()`。

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a> path:: has_root_name

返回 `!root_name().empty()`。

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a> path:: has_root_path

返回 `!root_path().empty()`。

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a> path::has_stem

返回 `!stem().empty()`。

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a> path:: is_absolute

对于 Windows，函数返回`has_root_name() && has_root_directory()`。 对于 Posix，函数将返回`has_root_directory()`。

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a> path:: is_relative

返回 `!is_absolute()`。

```cpp
bool is_relative() const;
```

## <a name="iterator"></a> path:: iterator

一个双向常量迭代器，它将指定的路径组件`myname`。

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>备注

此类描述了双向常量迭代器，指定`path`组件的`myname`序列中：

1. 根名称（如存在）

1. 根目录（如存在）

1. 父级的剩余目录元素`path`(如果有） 结尾的文件名，如存在

有关`pval`类型的对象`path`:

1. `path::iterator X = pval.begin()` 指定第一个`path`中的路径名，如果存在的元素。

1. `X == pval.end()` 为 true`X`点刚超出序列末尾的组件。

3. `*X` 返回与当前组件匹配的字符串

1. `++X` 指定序列中的下一个组件（如果存在）。

1. `--X` 指定序列中的前面的组件（如果存在）。

1. 更改`myname`使指定元素中的所有迭代器失效`myname`。

## <a name="make_preferred"></a> path:: make_preferred

将转换为每个分隔符`preferred_separator`根据需要。

```cpp
path& make_preferred();
```

## <a name="native"></a> path::native

返回 `myname`。

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a> path:: operator =

将路径的元素替换为另一个路径的副本。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>参数

*right*<br/>
[路径](../standard-library/path-class.md)复制到`path`。

*source*<br/>
源路径中。

### <a name="remarks"></a>备注

第一个成员运算符副本`right.myname`到`myname`。 第二个成员运算符将移`right.myname`到`myname`。 第三个成员运算符在行为上与相同`*this = path(source)`。

## <a name="op_add"></a> path:: operator + =

各种`concat`表达式。

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>参数

*right*<br/>
添加的路径。

*str*<br/>
已添加的字符串。

*ptr*<br/>
添加了的指针。

*Elem*<br/>
在添加`value_type`或`Elem`。

*source*<br/>
添加了的源。

### <a name="remarks"></a>备注

成员函数的行为与以下相应表达式相同：

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a> path:: operator / =

各种`append`表达式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>参数

*right*<br/>
添加的路径。

*source*<br/>
添加了的源。

### <a name="remarks"></a>备注

成员函数的行为与以下相应表达式相同：

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a> path:: operator string_type

返回 `myname`。

```cpp
operator string_type() const;
```

## <a name="parent_path"></a> path:: parent_path

返回父路径组件`myname`。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>备注

返回父路径组件`myname`，专门的前缀`myname`之后删除`filename().native()`和任何前面紧邻的目录分隔符。 (同样，如果`begin() != end()`，它是在范围内的所有元素的组合`[begin(), --end())`通过连续应用`operator/=`。)组件可能为空。

## <a name="path"></a> path:: path

构造`path`以各种方式。

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>参数

*right*<br/>
这些构造的路径将成为副本路径。

*source*<br/>
这些构造的路径将成为副本源。

*Loc*<br/>
指定的区域设置。

*first*<br/>
要复制的第一个元素的位置。

*最后一个*<br/>
要复制的最后一个元素的位置。

### <a name="remarks"></a>备注

所有构造的构造函数`myname`以各种方式：

有关`path()`它是`myname()`。

有关`path(const path& right`) 是`myname(right.myname)`。

有关`path(path&& right)`它是`myname(right.myname)`。

有关`template<class Source> path(const Source& source)`它是`myname(source)`。

有关`template<class Source> path(const Source& source, const locale& loc)`很`myname(source)`，获取任何所需的 codecvt 方面从`loc`。

有关`template<class InIt> path(InIt first, InIt last)`它是`myname(first, last)`。

有关`template<class InIt> path(InIt first, InIt last, const locale& loc)`很`myname(first, last)`，获取任何所需的 codecvt 方面从`loc`。

## <a name="preferred_separator"></a> path::preferred_separator

常量对象提供首选字符来分隔路径组件，具体取决于主机操作系统。

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume Posix
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>备注

请注意，在 Windows 下的大多数上下文中，同样允许在它的位置使用 L'/'。

## <a name="relative_path"></a> path:: relative_path

返回的相对路径组件`myname`。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>备注

返回的相对路径组成部分`myname`，专门的后缀`myname`之后删除`root_path().native()`和任何立即其后的冗余目录分隔符。 组件可能为空。

## <a name="remove_filename"></a> path:: remove_filename

删除文件名。

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a> path:: replace_extension

替换的扩展`myname`。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>参数

*将 newext*<br/>
新的扩展名。

### <a name="remarks"></a>备注

首先删除后缀`extension().native()`从`myname`。 然后，如果`!newext.empty() && newext[0] != dot`(其中`dot`是`*path(".").c_str()`)，然后`dot`追加到`myname`。 然后*将 newext*追加到`myname`。

## <a name="replace_filename"></a> path:: replace_filename

将替换文件名。

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>参数

*pval*<br/>
文件名的路径。

### <a name="remarks"></a>备注

成员函数执行：

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a> path:: root_directory

返回的根组件`myname`。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>备注

组件可能为空。

## <a name="root_name"></a> path:: root_name

返回的根名称组件`myname`。

```cpp
path root_name() const;
```

### <a name="remarks"></a>备注

组件可能为空。

## <a name="root_path"></a> path:: root_path

返回的根路径组件`myname`。

```cpp
path root_path() const;
```

### <a name="remarks"></a>备注

返回的根路径组件`myname`，具体而言`root_name()`  /  `root_directory`。 组件可能为空。

## <a name="stem"></a> path:: stem

返回`stem`组件的`myname`。

```cpp
path stem() const;
```

### <a name="remarks"></a>备注

返回`stem`组成部分`myname`，具体而言`filename().native()`任何尾随`extension().native()`中删除。 组件可能为空。

## <a name="string"></a> path:: string

将转换中存储的序列`mypath`。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>备注

第一个 （模板） 成员函数将转换中存储的序列`mypath`一样：

1. `string()` 的 `string<char, Traits, Alloc>()`

1. `wstring()` 的 `string<wchar_t, Traits, Alloc>()`

1. `u16string()` 的 `string<char16_t, Traits, Alloc>()`

1. `u32string()` 的 `string<char32_t, Traits, Alloc>()`

第二个成员函数将转换中存储的序列`mypath`到为主机系统偏好的编码**char**序列，并返回它存储在类型的对象`string`。

## <a name="string_type"></a> path::string_type

该类型是 `basic_string<value_type>` 的同义词。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a> path:: swap

执行`swap(mypath, right.mypath)`。

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a> path::u16string

将转换中存储的序列`mypath`utf-16 和存储中的类型的对象返回到`u16string`。

```cpp
u16string u16string() const;
```

## <a name="u32string"></a> path::u32string

将转换中存储的序列`mypath`UTF-32，它存储在类型的对象返回到`u32string`。

```cpp
u32string u32string() const;
```

## <a name="u8string"></a> path::u8string

将转换中存储的序列`mypath`utf-8，它存储在类型的对象返回到`u8string`。

```cpp
string u8string() const;
```

## <a name="value_type"></a> path::value_type

此类型描述`path`主机操作系统偏好的元素。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume Posix
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a> path::wstring

将转换中存储的序列`mypath`到为主机系统偏好的编码**wchar_t**序列，并返回它存储在类型的对象`wstring`。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
