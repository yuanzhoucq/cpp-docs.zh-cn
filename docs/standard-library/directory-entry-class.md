---
title: directory_entry 类
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: c1b68aefd44d8f0ac60c36307dee93333d801bb9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533817"
---
# <a name="directoryentry-class"></a>directory_entry 类

描述由 `*X` 返回的对象，其中 *X* 是 [directory_iterator](../standard-library/directory-iterator-class.md) 或 [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)。

## <a name="syntax"></a>语法

```cpp
class directory_entry;
```

## <a name="remarks"></a>备注

该类存储 [path](../standard-library/path-class.md) 类型的对象。 存储的 `path` 可以是 [path 类](../standard-library/path-class.md)的实例或从 `path` 派生的类型的实例。 它还存储两个 [file_type](../standard-library/filesystem-enumerations.md#file_type) 值；一个表示有关存储文件名的状态的已知信息，另一个表示有关文件名的符号链接状态的已知信息。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[directory_entry](#directory_entry)|默认构造函数行为符合预期。 第四个构造函数初始化`mypath`到*pval*，`mystat`到*stat_arg*，以及`mysymstat`到*symstat_arg*。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[assign](#assign)|成员函数将分配*pval*到`mypath`， *stat*到`mystat`，以及*将 symstat 分配*到`mysymstat`。|
|[path](#path)|成员函数返回 `mypath`。|
|[replace_filename](#replace_filename)|成员函数将替换`mypath`与`mypath.parent_path()`  /  *pval*，`mystat`与*stat_arg*，并`mysymstat`与*为 ymstat_arg*|
|[status](#status)|这两个成员函数返回`mystat`可能是第一次更改。|
|[symlink_status](#symlink_status)|这两个成员函数返回`mysymstat`可能是第一次更改。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](#op_neq)|用另一个列表的副本替换列表中的元素。|
|[operator=](#op_as)|默认成员赋值运算符的行为符合预期。|
|[operator==](#op_eq)|返回 `mypath == right.mypath`。|
|[operator<](#op_lt)|返回 `mypath < right.mypath`。|
|[operator<=](#op_lteq)|返回 `!(right < *this)`。|
|[operator>](#op_gt)|返回 `right < *this`。|
|[operator>=](#op_gteq)|返回 `!(*this < right)`。|
|[运算符 const path_type （& a)](#path_type)|返回 `mypath`。|

## <a name="requirements"></a>要求

**标头：** \<实验性/文件系统&gt;

**命名空间：** std::experimental::filesystem

## <a name="assign"></a> 分配

成员函数将分配*pval*到`mypath`， *stat_arg*到`mystat`，以及*symstat_arg*到`mysymstat`。

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>参数

*pval*<br/>
存储的文件名称路径。

*stat_arg*<br/>
存储的文件名称的状态。

*为 ymstat_arg*<br/>
存储的文件名称的符号链接状态。

## <a name="directory_entry"></a> directory_entry

默认构造函数行为符合预期。 第四个构造函数初始化`mypath`到*pval*，`mystat`到*stat_arg*，以及`mysymstat`到*symstat_arg*。

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>参数

*pval*<br/>
存储的文件名称路径。

*stat_arg*<br/>
存储的文件名称的状态。

*为 ymstat_arg*<br/>
存储的文件名称的符号链接状态。

## <a name="op_neq"></a> 运算符 ！ =

成员函数返回 `!(*this == right)`。

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)要进行比较的`directory_entry`。

## <a name="op_as"></a> 运算符 =

默认成员赋值运算符的行为符合预期。

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)复制到`directory_entry`。

## <a name="op_eq"></a> 运算符 = =

成员函数返回 `mypath == right.mypath`。

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)要进行比较的`directory_entry`。

## <a name="op_lt"></a> 运算符&lt;

成员函数返回 `mypath < right.mypath`。

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)要进行比较的`directory_entry`。

## <a name="op_lteq"></a> 运算符&lt;=

成员函数返回 `!(right < *this)`。

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)要进行比较的`directory_entry`。

## <a name="op_gt"></a> 运算符&gt;

成员函数返回 `right < *this`。

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)要进行比较的`directory_entry`。

## <a name="op_gteq"></a> 运算符&gt;=

成员函数返回 `!(*this < right)`。

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_entry](../standard-library/directory-entry-class.md)要进行比较的`directory_entry`。

## <a name="path_type"></a> 运算符 const path_type （& a)

该成员运算符将返回 `mypath`。

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a> 路径

成员函数返回 `mypath`。

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a> replace_filename

成员函数将替换`mypath`与`mypath.parent_path()`  /  *pval*，`mystat`与*stat_arg*，并`mysymstat`与*为 ymstat_arg*

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>参数

*pval*<br/>
存储的文件名称路径。

*stat_arg*<br/>
存储的文件名称的状态。

*为 ymstat_arg*<br/>
存储的文件名称的符号链接状态。

## <a name="status"></a> 状态

这两个成员函数返回`mystat`可能是第一次更改，如下所示：

1. 如果`status_known(mystat)`然后不执行任何操作。

1. 否则为如果`!status_known(mysymstat) && !is_symlink(mysymstat)`然后`mystat = mysymstat`。

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>参数

*ec*<br/>
状态错误代码。

## <a name="symlink_status"></a> symlink_status

这两个成员函数返回`mysymstat`可能是第一次更改，如下所示： 如果`status_known(mysymstat)`然后不执行任何操作。 否则为 `mysymstat = symlink_status(mypval)`。

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>参数

*ec*<br/>
状态错误代码。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem&gt;](../standard-library/filesystem.md)<br/>
