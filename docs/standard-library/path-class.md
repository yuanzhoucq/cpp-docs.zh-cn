---
title: path 类
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 0bc26bb04464c52ed08d46e6a12c12cae6909d6f
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898795"
---
# <a name="path-class"></a>path 类

**Path**类存储类型 `string_type`的对象，此对象称为 `myname` 此处用于处于阐释，适合用作路径名。 `string_type` 是 `basic_string<value_type>`的同义词，其中 `value_type`**是在 POSIX 上**的**wchar_t**的同义词。

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
|[迭代器](#iterator)|指定 `myname`的 `path` 组件的双向常量迭代器。|
|[string_type](#string_type)|该类型是 `basic_string<value_type>`的同义词。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[append](#append)|将指定序列追加到 `mypath`，根据需要转换和插入 preferred_separator。|
|[assign](#assign)|将 `mypath` 替换为指定的序列，并根据需要进行转换。|
|[begin](#begin)|返回一个 `path::iterator`，它指定路径名中的第一个路径元素（如果存在）。|
|[c_str](#c_str)|返回指向 `mypath`中第一个字符的指针。|
|[clear](#clear)|执行 `mypath.clear()`。|
|[compare](#compare)|返回比较值。|
|[concat](#compare)|根据需要，将指定序列追加到 `mypath`，转换（但不插入分隔符）。|
|[empty](#empty)|返回 `mypath.empty()`。|
|[end](#end)|返回 `iterator`类型的序列末尾迭代器。|
|[拓](#extension)|返回 `filename()`的后缀。|
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
|[is_absolute](#is_absolute)|对于 Windows，函数将返回 `has_root_name() && has_root_directory()`。 对于 POSIX，函数返回 `has_root_directory()`。|
|[is_relative](#is_relative)|返回 `!is_absolute()`。|
|[make_preferred](#make_preferred)|根据需要将每个分隔符转换为 preferred_separator。|
|[本机](#native)|返回 `myname`。|
|[parent_path](#parent_path)|返回 `myname`的父路径组件。|
|[preferred_separator](#preferred_separator)|常量对象提供首选字符来分隔路径组件，具体取决于主机操作系统。 |
|[relative_path](#relative_path)|返回 `myname`的相对路径组件。 |
|[remove_filename](#remove_filename)|删除文件名。|
|[replace_extension](#replace_extension)|替换 `myname`的扩展。 |
|[replace_filename](#replace_filename)|RReplaces 文件名。|
|[root_directory](#root_directory)|返回 `myname`的根目录组件。 |
|[root_name](#root_name)|返回 `myname`的根名称组件。 |
|[root_path](#root_path)|返回 `myname`的根路径组件。|
|[stem](#stem)|返回 `myname`的 `stem` 组件。|
|[string](#string)|转换 `mypath`中存储的序列。|
|[swap](#swap)|执行 `swap(mypath, right.mypath)`。|
|[u16string](#u16string)|将 `mypath` 中存储的序列转换为 UTF-16，并将其返回存储到 `u16string`类型的对象中。|
|[u32string](#u32string)|将 `mypath` 中存储的序列转换为 32 UTF-8，并将其返回存储在类型 `u32string`的对象中。|
|[u8string](#u8string)|将 `mypath` 中存储的序列转换为 UTF-8，并将其返回存储到 `u8string`类型的对象中。|
|[value_type](#value_type)|类型描述了主机操作系统偏好的路径元素。|
|[wstring](#wstring)|将 `mypath` 中存储的序列转换为 `wchar_t` 序列的主机系统所采用的编码，并将其返回存储到类型 `wstring`的对象中。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_as)|将路径的元素替换为另一个路径的副本。|
|[operator+=](#op_add)|各种 `concat` 表达式。|
|[operator/=](#op_divide)|各种 `append` 表达式。|
|[operator string_type](#op_string)|返回 `myname`。|

## <a name="requirements"></a>需求

**标头：** \<filesystem >

**命名空间：** std::experimental::filesystem

## <a name="append"></a>path：： append

将指定序列追加到 `mypath`，根据需要转换和插入 `preferred_separator`。

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*源*\
指定的序列。

*第一个*\
指定序列的开头。

*最后*\
指定序列的末尾。

## <a name="assign"></a>path：： assign

将 `mypath` 替换为指定的序列，并根据需要进行转换。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*源*\
指定的序列。

*第一个*\
指定序列的开头。

*最后*\
指定序列的末尾。

## <a name="begin"></a>path：： begin

返回一个 `path::iterator`，它指定路径名中的第一个路径元素（如果存在）。

```cpp
iterator begin() const;
```

## <a name="c_str"></a>path：： c_str

返回指向 `mypath`中第一个字符的指针。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>path：： clear

执行 `mypath.clear()`。

```cpp
void clear() noexcept;
```

## <a name="compare"></a>path：： compare

第一个函数返回 `mypath.compare(pval.native())`。 第二个函数返回 `mypath.compare(str)`。 第三个函数返回 `mypath.compare(ptr)`。

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>参数

*pval*\
要比较的路径。

*str*\
要比较的字符串。

*ptr*\
要比较的指针。

## <a name="concat"></a>path：： concat

根据需要，将指定序列追加到 `mypath`，转换（但不插入分隔符）。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*源*\
指定的序列。

*第一个*\
指定序列的开头。

*最后*\
指定序列的末尾。

## <a name="const_iterator"></a>path：： const_iterator

`iterator` 的同义词。

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>路径：： empty

返回 `mypath.empty()`。

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>path：： end

返回 `iterator`类型的序列末尾迭代器。

```cpp
iterator end() const;
```

## <a name="extension"></a>path：： extension

返回 `filename()`的后缀。

```cpp
path extension() const;
```

### <a name="remarks"></a>备注

返回 `filename() X` 的后缀，如下所示：

如果 `X == path(".") || X == path("..")` 或 `X` 不包含任何点，则后缀为空。

否则，前缀以最右侧的点开头（并将其包含在内）。

## <a name="filename"></a>path：： filename

返回 myname 的根目录组件，尤其是 `empty() path() : *--end()`。 组件可能为空。

```cpp
path filename() const;
```

## <a name="generic_string"></a>path：： generic_string

返回 `this->string<Elem, Traits, Alloc>(al)` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>path：： generic_u16string

返回 `u16string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a>path：： generic_u32string

返回 `u32string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a>path：： generic_u8string

返回 `u8string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>path：： generic_wstring

返回 `wstring()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>path：： has_extension

返回 `!extension().empty()`。

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>path：： has_filename

返回 `!filename().empty()`。

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>path：： has_parent_path

返回 `!parent_path().empty()`。

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>path：： has_relative_path

返回 `!relative_path().empty()`。

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>path：： has_root_directory

返回 `!root_directory().empty()`。

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>path：： has_root_name

返回 `!root_name().empty()`。

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>path：： has_root_path

返回 `!root_path().empty()`。

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>path：： has_stem

返回 `!stem().empty()`。

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>path：： is_absolute

对于 Windows，函数将返回 `has_root_name() && has_root_directory()`。 对于 POSIX，函数返回 `has_root_directory()`。

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>path：： is_relative

返回 `!is_absolute()`。

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>path：： iterator

指定 `myname`的路径组件的双向常量迭代器。

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

类描述了一个双向常量迭代器，该迭代器指定序列中 `myname` 的 `path` 组件：

1. 根名称（如存在）

1. 根目录（如存在）

1. 父 `path`的其余目录元素（如果存在），以文件名结尾（如果存在）

对于 `pval` `path`类型的对象：

1. `path::iterator X = pval.begin()` 指定路径名中的第一个 `path` 元素（如果存在）。

1. 当 `X` 点刚刚超过组件序列的末尾时，`X == pval.end()` 为 true。

3. `*X` 返回与当前组件匹配的字符串

1. `++X` 指定序列中的下一个组件（如果存在）。

1. `--X` 指定序列中的前面的组件（如果存在）。

1. 更改 `myname` 使在 `myname`中指定元素的所有迭代器失效。

## <a name="make_preferred"></a>path：： make_preferred

根据需要将每个分隔符转换为 `preferred_separator`。

```cpp
path& make_preferred();
```

## <a name="native"></a>路径：： native

返回 `myname`。

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a>path：： operator =

将路径的元素替换为另一个路径的副本。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>参数

*right*\
要复制到`path`中的[路径](../standard-library/path-class.md)。

*源*\
源路径。

### <a name="remarks"></a>备注

第一个成员运算符将 `right.myname` 复制到 `myname`。 第二个成员运算符将 `right.myname` 移动到 `myname`中。 第三个成员运算符与 `*this = path(source)`的行为相同。

## <a name="op_add"></a>path：： operator + =

各种 `concat` 表达式。

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

*right*\
添加的路径。

*str*\
添加的字符串。

*ptr*\
添加的指针。

*elem*\
添加的 `value_type` 或 `Elem`。

*源*\
添加的源。

### <a name="remarks"></a>备注

成员函数的行为与以下相应表达式相同：

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a>path：： operator/=

各种 `append` 表达式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>参数

*right*\
添加的路径。

*源*\
添加的源。

### <a name="remarks"></a>备注

成员函数的行为与以下相应表达式相同：

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>path：： operator string_type

返回 `myname`。

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>路径：:p arent_path

返回 `myname`的父路径组件。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>备注

返回 `myname`的父路径组件，尤其是删除 `filename().native()` 之前 `myname` 的前缀和任何前面紧邻的目录分隔符。 （同样，如果 `begin() != end()`，它将通过连续应用 `operator/=`将 `[begin(), --end())` 范围内的所有元素组合在一起。）组件可能为空。

## <a name="path"></a>路径：:p a

以多种方式构造 `path`。

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

*right*\
构造的路径要作为其副本的路径。

*源*\
构造的路径要作为其副本的源。

*loc*\
指定的区域设置。

*第一个*\
要复制的第一个元素的位置。

*最后*\
要复制的最后一个元素的位置。

### <a name="remarks"></a>备注

构造函数均以各种方式构造 `myname`：

对于 `path()` `myname()`。

对于 `path(const path& right`），`myname(right.myname)`。

对于 `path(path&& right)` `myname(right.myname)`。

对于 `template<class Source> path(const Source& source)` `myname(source)`。

对于 `template<class Source> path(const Source& source, const locale& loc)` `myname(source)`，从 `loc`获取所需的任何 codecvt 方面。

对于 `template<class InIt> path(InIt first, InIt last)` `myname(first, last)`。

对于 `template<class InIt> path(InIt first, InIt last, const locale& loc)` `myname(first, last)`，从 `loc`获取所需的任何 codecvt 方面。

## <a name="preferred_separator"></a>路径：:p referred_separator

常量对象提供首选字符来分隔路径组件，具体取决于主机操作系统。

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>备注

请注意，在 Windows 下的大多数上下文中，同样允许在它的位置使用 L'/'。

## <a name="relative_path"></a>path：： relative_path

返回 `myname`的相对路径组件。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>备注

返回 `myname`的相对路径组件，尤其是删除 `root_path().native()` 和任何紧随其后的冗余目录分隔符后 `myname` 的后缀。 组件可能为空。

## <a name="remove_filename"></a>path：： remove_filename

删除文件名。

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a>path：： replace_extension

替换 `myname`的扩展。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>参数

*newext*\
新扩展。

### <a name="remarks"></a>备注

首先从 `myname`中删除后缀 `extension().native()`。 如果 `!newext.empty() && newext[0] != dot` （其中 `dot` `*path(".").c_str()`），则 `dot` 将追加到 `myname`。 然后将*newext*追加到 `myname`。

## <a name="replace_filename"></a>path：： replace_filename

替换文件名。

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>参数

*pval*\
文件名的路径。

### <a name="remarks"></a>备注

成员函数执行：

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a>path：： root_directory

返回 `myname`的根目录组件。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>备注

组件可能为空。

## <a name="root_name"></a>path：： root_name

返回 `myname`的根名称组件。

```cpp
path root_name() const;
```

### <a name="remarks"></a>备注

组件可能为空。

## <a name="root_path"></a>path：： root_path

返回 `myname`的根路径组件。

```cpp
path root_path() const;
```

### <a name="remarks"></a>备注

返回 `myname`的根路径组件，尤其是 `root_name()` / `root_directory`。 组件可能为空。

## <a name="stem"></a>path：：词干

返回 `myname`的 `stem` 组件。

```cpp
path stem() const;
```

### <a name="remarks"></a>备注

返回 `myname`的 `stem` 组件，尤其是删除了任何尾随 `extension().native()` `filename().native()`。 组件可能为空。

## <a name="string"></a>path：： string

转换 `mypath`中存储的序列。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>备注

第一个（模板）成员函数按与相同的方式转换中存储的序列 `mypath`：

1. 对于 `string<char, Traits, Alloc>()`，为 `string()`

1. 对于 `string<wchar_t, Traits, Alloc>()`，为 `wstring()`

1. 对于 `string<char16_t, Traits, Alloc>()`，为 `u16string()`

1. 对于 `string<char32_t, Traits, Alloc>()`，为 `u32string()`

第二个成员函数将 `mypath` 中存储的序列转换为**char**序列的主机系统所采用的编码，并将其返回存储在类型 `string`的对象中。

## <a name="string_type"></a>path：： string_type

该类型是 `basic_string<value_type>`的同义词。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a>path：： swap

执行 `swap(mypath, right.mypath)`。

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>path：： u16string

将 `mypath` 中存储的序列转换为 UTF-16，并将其返回存储到 `u16string`类型的对象中。

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>path：： u32string

将 `mypath` 中存储的序列转换为 32 UTF-8，并将其返回存储在类型 `u32string`的对象中。

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>path：： u8string

将 `mypath` 中存储的序列转换为 UTF-8，并将其返回存储到 `u8string`类型的对象中。

```cpp
string u8string() const;
```

## <a name="value_type"></a>path：： value_type

类型描述了主机操作系统欢迎使用的 `path` 元素。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>path：： wstring

将 `mypath` 中存储的序列转换为**wchar_t**序列的主机系统所采用的编码，并将其返回存储到类型 `wstring`的对象中。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
