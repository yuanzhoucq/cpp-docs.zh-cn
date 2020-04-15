---
title: path 类
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 669dfd2c8cd8576ebfb6684bab7cf63cdd51babc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372108"
---
# <a name="path-class"></a>path 类

**路径**类存储类型的对象`string_type`，此处称为`myname`"公开"，适合用作路径名称。 `string_type``basic_string<value_type>`是 的同义词，`value_type`其中是 windows 上**wchar_t**的同义词，或 POSIX 上的**字符**的同义词。

有关详细信息和代码示例，请参阅[文件系统导航 （C++）](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>语法

```cpp
class path;
```

### <a name="constructors"></a>构造函数

|构造函数|说明|
|-|-|
|[路径](#path)|构造一个 `path`。|

### <a name="typedefs"></a>Typedef

|类型名称|说明|
|-|-|
|[const_iterator](#const_iterator)|`iterator` 的同义词。|
|[迭 代](#iterator)|指定 的双向常量迭代器，`path`用于指定 的`myname`组件。|
|[string_type](#string_type)|该类型是 `basic_string<value_type>` 的同义词。|

### <a name="member-functions"></a>成员职能

|成员函数|说明|
|-|-|
|[append](#append)|根据需要将指定的序列追加到`mypath`，并根据需要转换并插入preferred_separator。|
|[分配](#assign)|`mypath`替换为指定的序列，根据需要转换。|
|[开始](#begin)|返回指定`path::iterator`路径名称中的第一个路径元素（如果存在）。|
|[c_str](#c_str)|返回指向 中第一个字符的`mypath`指针。|
|[清楚](#clear)|执行`mypath.clear()`。|
|[比较](#compare)|返回比较值。|
|[Concat](#compare)|根据需要将指定的序列追加到`mypath`转换（但不插入分隔符）。|
|[空](#empty)|返回 `mypath.empty()`。|
|[结束](#end)|返回类型`iterator`序列结束迭代器。|
|[扩展](#extension)|返回 的`filename()`后缀。|
|[文件名](#filename)|返回 myname 的根目录组件，尤其是 `empty() path() : *--end()`。 组件可能为空。|
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
|[is_absolute](#is_absolute)|对于 Windows，函数将`has_root_name() && has_root_directory()`返回 。 对于 POSIX，函数返回`has_root_directory()`。|
|[is_relative](#is_relative)|返回 `!is_absolute()`。|
|[make_preferred](#make_preferred)|根据需要将每个分隔符转换为preferred_separator。|
|[本地](#native)|返回 `myname`。|
|[parent_path](#parent_path)|返回 的`myname`父路径组件。|
|[preferred_separator](#preferred_separator)|常量对象提供首选字符来分隔路径组件，具体取决于主机操作系统。 |
|[relative_path](#relative_path)|返回`myname`的相对路径组件。 |
|[remove_filename](#remove_filename)|删除文件名。|
|[replace_extension](#replace_extension)|替换 的`myname`扩展。 |
|[replace_filename](#replace_filename)|R 替换文件名。|
|[root_directory](#root_directory)|返回 的`myname`根目录组件。 |
|[root_name](#root_name)|返回 的`myname`根名称组件。 |
|[root_path](#root_path)|返回 的`myname`根路径组件。|
|[stem](#stem)|返回`stem`的`myname`组件。|
|[string](#string)|转换存储在 中的`mypath`序列。|
|[交换](#swap)|执行`swap(mypath, right.mypath)`。|
|[u16字符串](#u16string)|将存储在 中的`mypath`序列转换为 UTF-16，并将其返回存储在类型`u16string`对象中。|
|[u32字符串](#u32string)|将存储在 中的`mypath`序列转换为 UTF-32，并将其返回存储在类型`u32string`对象中。|
|[u8字符串](#u8string)|将存储在 中的`mypath`序列转换为 UTF-8，并将其返回存储在类型`u8string`对象中。|
|[value_type](#value_type)|类型描述了主机操作系统偏好的路径元素。|
|[wstring](#wstring)|将存储在中的`mypath`序列转换为主机系统对`wchar_t`序列所青睐的编码，并将其返回存储在类型`wstring`对象中。|

### <a name="operators"></a>运算符

|操作员|说明|
|-|-|
|[运算符*](#op_as)|将路径的元素替换为另一个路径的副本。|
|[运算符*](#op_add)|各种`concat`表达式。|
|[操作员/*](#op_divide)|各种`append`表达式。|
|[运算符string_type](#op_string)|返回 `myname`。|

## <a name="requirements"></a>要求

**标题：**\<文件系统>

**命名空间：** std::experimental::filesystem

## <a name="pathappend"></a><a name="append"></a>路径：：追加

根据需要将指定的序列追加到`mypath`，并根据需要插入`preferred_separator`。

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*源*\
指定序列。

*第一*\
指定序列的开始。

*最后*\
指定序列的结束。

## <a name="pathassign"></a><a name="assign"></a>路径：：分配

`mypath`替换为指定的序列，根据需要转换。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*源*\
指定序列。

*第一*\
指定序列的开始。

*最后*\
指定序列的结束。

## <a name="pathbegin"></a><a name="begin"></a>路径：：开始

返回指定`path::iterator`路径名称中的第一个路径元素（如果存在）。

```cpp
iterator begin() const;
```

## <a name="pathc_str"></a><a name="c_str"></a>路径：：c_str

返回指向 中第一个字符的`mypath`指针。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="pathclear"></a><a name="clear"></a>路径：：清除

执行`mypath.clear()`。

```cpp
void clear() noexcept;
```

## <a name="pathcompare"></a><a name="compare"></a>路径：：比较

第一个函数返回 `mypath.compare(pval.native())`。 第二个函数返回 `mypath.compare(str)`。 第三个函数`mypath.compare(ptr)`返回 。

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>参数

*普瓦尔*\
要比较的路径。

*Str*\
要比较的字符串。

*Ptr*\
要比较的指针。

## <a name="pathconcat"></a><a name="concat"></a>路径：：concat

根据需要将指定的序列追加到`mypath`转换（但不插入分隔符）。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>参数

*源*\
指定序列。

*第一*\
指定序列的开始。

*最后*\
指定序列的结束。

## <a name="pathconst_iterator"></a><a name="const_iterator"></a>路径：：const_iterator

`iterator` 的同义词。

```cpp
typedef iterator const_iterator;
```

## <a name="pathempty"></a><a name="empty"></a>路径：：空

返回 `mypath.empty()`。

```cpp
bool empty() const noexcept;
```

## <a name="pathend"></a><a name="end"></a>路径：：结束

返回类型`iterator`序列结束迭代器。

```cpp
iterator end() const;
```

## <a name="pathextension"></a><a name="extension"></a>路径：：扩展

返回 的`filename()`后缀。

```cpp
path extension() const;
```

### <a name="remarks"></a>备注

返回以下项的`filename() X`后缀：：

如果`X == path(".") || X == path("..")`或`X`不包含点，则后缀为空。

否则，前缀以最右侧的点开头（并将其包含在内）。

## <a name="pathfilename"></a><a name="filename"></a>路径：：文件名

返回 myname 的根目录组件，尤其是 `empty() path() : *--end()`。 组件可能为空。

```cpp
path filename() const;
```

## <a name="pathgeneric_string"></a><a name="generic_string"></a>路径：：generic_string

返回 `this->string<Elem, Traits, Alloc>(al)` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="pathgeneric_u16string"></a><a name="generic_u16string"></a>路径：：generic_u16string

返回 `u16string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
u16string generic_u16string() const;
```

## <a name="pathgeneric_u32string"></a><a name="generic_u32string"></a>路径：：generic_u32string

返回 `u32string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
u32string generic_u32string() const;
```

## <a name="pathgeneric_u8string"></a><a name="generic_u8string"></a>路径：：generic_u8string

返回 `u8string()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
string generic_u8string() const;
```

## <a name="pathgeneric_wstring"></a><a name="generic_wstring"></a>路径：：generic_wstring

返回 `wstring()` ，其中（在 Windows 下）任何反斜杠均转换为正斜杠。

```cpp
wstring generic_wstring() const;
```

## <a name="pathhas_extension"></a><a name="has_extension"></a>路径：：has_extension

返回 `!extension().empty()`。

```cpp
bool has_extension() const;
```

## <a name="pathhas_filename"></a><a name="has_filename"></a>路径：：has_filename

返回 `!filename().empty()`。

```cpp
bool has_filename() const;
```

## <a name="pathhas_parent_path"></a><a name="has_parent_path"></a>路径：：has_parent_path

返回 `!parent_path().empty()`。

```cpp
bool has_parent_path() const;
```

## <a name="pathhas_relative_path"></a><a name="has_relative_path"></a>路径：：has_relative_path

返回 `!relative_path().empty()`。

```cpp
bool has_relative_path() const;
```

## <a name="pathhas_root_directory"></a><a name="has_root_directory"></a>路径：：has_root_directory

返回 `!root_directory().empty()`。

```cpp
bool has_root_directory() const;
```

## <a name="pathhas_root_name"></a><a name="has_root_name"></a>路径：：has_root_name

返回 `!root_name().empty()`。

```cpp
bool has_root_name() const;
```

## <a name="pathhas_root_path"></a><a name="has_root_path"></a>路径：：has_root_path

返回 `!root_path().empty()`。

```cpp
bool has_root_path() const;
```

## <a name="pathhas_stem"></a><a name="has_stem"></a>路径：：has_stem

返回 `!stem().empty()`。

```cpp
bool has_stem() const;
```

## <a name="pathis_absolute"></a><a name="is_absolute"></a>路径：：is_absolute

对于 Windows，函数将`has_root_name() && has_root_directory()`返回 。 对于 POSIX，函数返回`has_root_directory()`。

```cpp
bool is_absolute() const;
```

## <a name="pathis_relative"></a><a name="is_relative"></a>路径：：is_relative

返回 `!is_absolute()`。

```cpp
bool is_relative() const;
```

## <a name="pathiterator"></a><a name="iterator"></a>路径：迭代器

指定 的双向常量迭代器，用于指定 的`myname`路径组件。

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

类描述一个双向常量迭代器，该迭代器在序列`path`中指定`myname`的组件：

1. 根名称（如存在）

1. 根目录（如存在）

1. 父`path`目录元素（如果存在）以文件名结尾（如果存在）

对于`pval`类型`path`的对象：

1. `path::iterator X = pval.begin()`指定路径名称中`path`的第一个元素（如果存在）。

1. `X == pval.end()`当点刚刚`X`超过组件序列的末尾时，为 true。

1. `*X`返回与当前组件匹配的字符串

1. `++X` 指定序列中的下一个组件（如果存在）。

1. `--X` 指定序列中的前面的组件（如果存在）。

1. 更改`myname`会使指定元素的所有`myname`迭代器无效。

## <a name="pathmake_preferred"></a><a name="make_preferred"></a>路径：：make_preferred

根据需要将每个分隔符转换为 。 `preferred_separator`

```cpp
path& make_preferred();
```

## <a name="pathnative"></a><a name="native"></a>路径：：本机

返回 `myname`。

```cpp
const string_type& native() const noexcept;
```

## <a name="pathoperator"></a><a name="op_as"></a>路径：：运算符*

将路径的元素替换为另一个路径的副本。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>参数

*对*\
复制到 的[路径](../standard-library/path-class.md)。 `path`

*源*\
源路径。

### <a name="remarks"></a>备注

第一个成员运算符复制到`right.myname``myname`。 第二个成员运算符将`right.myname`移动到`myname`。 第三个成员运算符的操作与 相同`*this = path(source)`。

## <a name="pathoperator"></a><a name="op_add"></a>路径：：运算符*

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

*对*\
添加的路径。

*Str*\
添加的字符串。

*Ptr*\
添加的指针。

*埃莱姆*\
添加`value_type`的`Elem`或 。

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

## <a name="pathoperator"></a><a name="op_divide"></a>路径：：运算符/*

各种`append`表达式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>参数

*对*\
添加的路径。

*源*\
添加的源。

### <a name="remarks"></a>备注

成员函数的行为与以下相应表达式相同：

1. `append(right);`

1. `append(source);`

## <a name="pathoperator-string_type"></a><a name="op_string"></a>路径：：运算符string_type

返回 `myname`。

```cpp
operator string_type() const;
```

## <a name="pathparent_path"></a><a name="parent_path"></a>路径：:p

返回 的`myname`父路径组件。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>备注

返回 的`myname`父路径组件 ，特别是删除`myname``filename().native()`后和任何紧邻目录分隔符的前缀。 （同样，如果`begin() != end()`，它是通过连续应用`[begin(), --end())``operator/=`（） 来组合范围内的所有元素。组件可能为空。

## <a name="pathpath"></a><a name="path"></a>路径：:p

以各种方式构造`path`。

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

*对*\
构造路径为副本的路径。

*源*\
构造路径为副本的源。

*loc*\
指定的区域设置。

*第一*\
要复制的第一个元素的位置。

*最后*\
要复制的最后一个元素的位置。

### <a name="remarks"></a>备注

构造函数都以各种方式构造`myname`：

因为它是`path()` `myname()`。

因为`path(const path& right`）`myname(right.myname)`它是 。

因为它是`path(path&& right)` `myname(right.myname)`。

因为它是`template<class Source> path(const Source& source)` `myname(source)`。

因为它是`template<class Source> path(const Source& source, const locale& loc)` `myname(source)`，从`loc`获取任何所需的编解码法分面。

因为它是`template<class InIt> path(InIt first, InIt last)` `myname(first, last)`。

因为它是`template<class InIt> path(InIt first, InIt last, const locale& loc)` `myname(first, last)`，从`loc`获取任何所需的编解码法分面。

## <a name="pathpreferred_separator"></a><a name="preferred_separator"></a>路径：:p引用分离器

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

## <a name="pathrelative_path"></a><a name="relative_path"></a>路径：：relative_path

返回`myname`的相对路径组件。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>备注

返回 的相对路径组件`myname`，特别是删除`root_path().native()`后的任何后续冗`myname`余目录分隔符的后缀。 组件可能为空。

## <a name="pathremove_filename"></a><a name="remove_filename"></a>路径：：remove_filename

删除文件名。

```cpp
path& remove_filename();
```

## <a name="pathreplace_extension"></a><a name="replace_extension"></a>路径：：replace_extension

替换 的`myname`扩展。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>参数

*纽埃斯特*\
新的扩展。

### <a name="remarks"></a>备注

首先从`myname`中删除后缀`extension().native()`。 然后，`!newext.empty() && newext[0] != dot`如果（`dot`位置`*path(".").c_str()`），则`dot`追加到`myname`。 然后 *，将 newext* `myname`追加到 。

## <a name="pathreplace_filename"></a><a name="replace_filename"></a>路径：：replace_filename

替换文件名。

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>参数

*普瓦尔*\
文件名的路径。

### <a name="remarks"></a>备注

成员函数执行：

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="pathroot_directory"></a><a name="root_directory"></a>路径：：root_directory

返回 的`myname`根目录组件。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>备注

组件可能为空。

## <a name="pathroot_name"></a><a name="root_name"></a>路径：：root_name

返回 的`myname`根名称组件。

```cpp
path root_name() const;
```

### <a name="remarks"></a>备注

组件可能为空。

## <a name="pathroot_path"></a><a name="root_path"></a>路径：：root_path

返回 的`myname`根路径组件。

```cpp
path root_path() const;
```

### <a name="remarks"></a>备注

返回 的根路径组件`myname`，`root_name()` / `root_directory`具体 。 组件可能为空。

## <a name="pathstem"></a><a name="stem"></a>路径：stem

返回`stem`的`myname`组件。

```cpp
path stem() const;
```

### <a name="remarks"></a>备注

返回`stem`的`myname`组件，特别是`filename().native()`删除任何尾随`extension().native()`的组件。 组件可能为空。

## <a name="pathstring"></a><a name="string"></a>路径：字符串

转换存储在 中的`mypath`序列。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>备注

第一个（模板）成员函数以与以下方式转换`mypath`存储的序列：

1. 若 `string<char, Traits, Alloc>()`，表示集 `string()`

1. 若 `string<wchar_t, Traits, Alloc>()`，表示集 `wstring()`

1. 若 `string<char16_t, Traits, Alloc>()`，表示集 `u16string()`

1. 若 `string<char32_t, Traits, Alloc>()`，表示集 `u32string()`

第二个成员函数将存储在中的`mypath`序列转换为主机系统为**字符**序列所青睐的编码，并将其返回存储在类型`string`对象中。

## <a name="pathstring_type"></a><a name="string_type"></a>路径：：string_type

该类型是 `basic_string<value_type>` 的同义词。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="pathswap"></a><a name="swap"></a>路径：：交换

执行`swap(mypath, right.mypath)`。

```cpp
void swap(path& right) noexcept;
```

## <a name="pathu16string"></a><a name="u16string"></a>路径：：u16字符串

将存储在 中的`mypath`序列转换为 UTF-16，并将其返回存储在类型`u16string`对象中。

```cpp
u16string u16string() const;
```

## <a name="pathu32string"></a><a name="u32string"></a>路径：：u32字符串

将存储在 中的`mypath`序列转换为 UTF-32，并将其返回存储在类型`u32string`对象中。

```cpp
u32string u32string() const;
```

## <a name="pathu8string"></a><a name="u8string"></a>路径：：u8字符串

将存储在 中的`mypath`序列转换为 UTF-8，并将其返回存储在类型`u8string`对象中。

```cpp
string u8string() const;
```

## <a name="pathvalue_type"></a><a name="value_type"></a>路径：：value_type

类型描述主机操作系统`path`青睐的元素。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="pathwstring"></a><a name="wstring"></a>路径：：wstring

将存储在中的`mypath`序列转换为主机系统对**wchar_t**序列所青睐的编码，并将其返回存储在类型`wstring`对象中。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>另请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
