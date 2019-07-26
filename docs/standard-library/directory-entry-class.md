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
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458963"
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
|[directory_entry](#directory_entry)|默认构造函数行为符合预期。 第四个构造`mypath`函数将初始化`mystat`为*pval*、 *stat_arg* `mysymstat`和*symstat_arg*。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[assign](#assign)|成员函数将*pval* `mypath`、 *stat* to `mystat`和*将 symstat 分配* `mysymstat`赋给。|
|[path](#path)|成员函数返回 `mypath`。|
|[replace_filename](#replace_filename)|该成员函数将`mypath`替换`mypath.parent_path()`为 / pval `mystat` 、 *stat_arg*和*symstat_arg*  `mysymstat`|
|[status](#status)|这两个成员`mystat`函数可能第一次被更改。|
|[symlink_status](#symlink_status)|这两个成员`mysymstat`函数可能第一次被更改。|

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
|[operator const path_type &](#path_type)|返回 `mypath`。|

## <a name="requirements"></a>要求

**标头:** \<实验性/文件系统&gt;

**命名空间：** std::experimental::filesystem

## <a name="assign"></a>将

成员函数将*pval* `mypath`、 *stat_arg* `mystat`和*symstat_arg* `mysymstat`分配给。

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>参数

*pval*\
存储的文件名路径。

*stat_arg*\
存储的文件名的状态。

*symstat_arg*\
存储的文件名的符号链接状态。

## <a name="directory_entry"></a>directory_entry

默认构造函数行为符合预期。 第四个构造`mypath`函数将初始化`mystat`为*pval*、 *stat_arg* `mysymstat`和*symstat_arg*。

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>参数

*pval*\
存储的文件名路径。

*stat_arg*\
存储的文件名的状态。

*symstat_arg*\
存储的文件名的符号链接状态。

## <a name="op_neq"></a>operator! =

成员函数返回 `!(*this == right)`。

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*然后*\
要[](../standard-library/directory-entry-class.md)与进行`directory_entry`比较的 directory_entry。

## <a name="op_as"></a>operator =

默认成员赋值运算符的行为符合预期。

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>参数

*然后*\
要[](../standard-library/directory-entry-class.md)复制到`directory_entry`中的 directory_entry。

## <a name="op_eq"></a>operator = =

成员函数返回 `mypath == right.mypath`。

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*然后*\
要[](../standard-library/directory-entry-class.md)与进行`directory_entry`比较的 directory_entry。

## <a name="op_lt"></a> 运算符&lt;

成员函数返回 `mypath < right.mypath`。

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*然后*\
要[](../standard-library/directory-entry-class.md)与进行`directory_entry`比较的 directory_entry。

## <a name="op_lteq"></a>操作员&lt;=

成员函数返回 `!(right < *this)`。

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*然后*\
要[](../standard-library/directory-entry-class.md)与进行`directory_entry`比较的 directory_entry。

## <a name="op_gt"></a> 运算符&gt;

成员函数返回 `right < *this`。

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*然后*\
要[](../standard-library/directory-entry-class.md)与进行`directory_entry`比较的 directory_entry。

## <a name="op_gteq"></a>操作员&gt;=

成员函数返回 `!(*this < right)`。

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>参数

*然后*\
要[](../standard-library/directory-entry-class.md)与进行`directory_entry`比较的 directory_entry。

## <a name="path_type"></a>operator const path_type &

该成员运算符将返回 `mypath`。

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>通道

成员函数返回 `mypath`。

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

该成员函数将`mypath`替换`mypath.parent_path()`为 / pval `mystat` 、 *stat_arg*和*symstat_arg*  `mysymstat`

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>参数

*pval*\
存储的文件名路径。

*stat_arg*\
存储的文件名的状态。

*symstat_arg*\
存储的文件名的符号链接状态。

## <a name="status"></a>状态值

这两个成员`mystat`函数可能首先更改, 如下所示:

1. 如果`status_known(mystat)`不执行任何操作。

1. 否则, 如果`!status_known(mysymstat) && !is_symlink(mysymstat)` `mystat = mysymstat`为, 则为。

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>参数

*欧洲*\
状态错误代码。

## <a name="symlink_status"></a>symlink_status

这两个成员`mysymstat`函数可能首先更改, 如下所示:如果`status_known(mysymstat)`不执行任何操作。 否则为 `mysymstat = symlink_status(mypval)`。

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>参数

*欧洲*\
状态错误代码。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem&gt;](../standard-library/filesystem.md)
