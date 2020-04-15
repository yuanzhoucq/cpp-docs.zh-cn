---
title: '&lt;filesystem&gt; 函数'
ms.date: 03/27/2019
f1_keywords:
- FILESYSTEM/std::experimental::filesystem::absolute
- FILESYSTEM/std::experimental::filesystem::canonical
- FILESYSTEM/std::experimental::filesystem::copy
- FILESYSTEM/std::experimental::filesystem::copy_file
- FILESYSTEM/std::experimental::filesystem::copy_symlink
- FILESYSTEM/std::experimental::filesystem::create_directories
- FILESYSTEM/std::experimental::filesystem::create_directory
- FILESYSTEM/std::experimental::filesystem::create_directory_symlink
- FILESYSTEM/std::experimental::filesystem::create_hard_link
- FILESYSTEM/std::experimental::filesystem::create_symlink
- FILESYSTEM/std::experimental::filesystem::current_path
- FILESYSTEM/std::experimental::filesystem::equivalent
- FILESYSTEM/std::experimental::filesystem::exists
- FILESYSTEM/std::experimental::filesystem::file_size
- FILESYSTEM/std::experimental::filesystem::hard_link_count
- FILESYSTEM/std::experimental::filesystem::hash_value
- FILESYSTEM/std::experimental::filesystem::is_block_file
- FILESYSTEM/std::experimental::filesystem::is_character_file
- FILESYSTEM/std::experimental::filesystem::is_directory
- FILESYSTEM/std::experimental::filesystem::is_empty
- FILESYSTEM/std::experimental::filesystem::is_fifo
- FILESYSTEM/std::experimental::filesystem::is_other
- FILESYSTEM/std::experimental::filesystem::is_regular_file
- FILESYSTEM/std::experimental::filesystem::is_socket
- FILESYSTEM/std::experimental::filesystem::is_symlink
- FILESYSTEM/std::experimental::filesystem::last_write_time
- FILESYSTEM/std::experimental::filesystem::permissions
- FILESYSTEM/std::experimental::filesystem::read_symlink
- FILESYSTEM/std::experimental::filesystem::remove
- FILESYSTEM/std::experimental::filesystem::remove_all
- FILESYSTEM/std::experimental::filesystem::rename
- FILESYSTEM/std::experimental::filesystem::resize_file
- FILESYSTEM/std::experimental::filesystem::space
- FILESYSTEM/std::experimental::filesystem::status
- FILESYSTEM/std::experimental::filesystem::status_known
- FILESYSTEM/std::experimental::filesystem::swap
- FILESYSTEM/std::experimental::filesystem::symlink_status
- FILESYSTEM/std::experimental::filesystem::system_complete
- FILESYSTEM/std::experimental::filesystem::temp_directory_path
- FILESYSTEM/std::experimental::filesystem::u8path
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
helpviewer_keywords:
- std::experimental::filesystem::absolute
- std::experimental::filesystem::canonical
- std::experimental::filesystem::copy
- std::experimental::filesystem::copy_file
- std::experimental::filesystem::copy_symlink
- std::experimental::filesystem::create_directories
- std::experimental::filesystem::create_directory
- std::experimental::filesystem::create_directory_symlink
- std::experimental::filesystem::create_hard_link
- std::experimental::filesystem::create_symlink
- std::experimental::filesystem::current_path
- std::experimental::filesystem::equivalent
- std::experimental::filesystem::exists
- std::experimental::filesystem::file_size
- std::experimental::filesystem::hard_link_count
- std::experimental::filesystem::hash_value
- std::experimental::filesystem::is_block_file
- std::experimental::filesystem::is_character_file
- std::experimental::filesystem::is_directory
- std::experimental::filesystem::is_empty
- std::experimental::filesystem::is_fifo
- std::experimental::filesystem::is_other
- std::experimental::filesystem::is_regular_file
- std::experimental::filesystem::is_socket
- std::experimental::filesystem::is_symlink
- std::experimental::filesystem::last_write_time
- std::experimental::filesystem::permissions
- std::experimental::filesystem::read_symlink
- std::experimental::filesystem::remove
- std::experimental::filesystem::remove_all
- std::experimental::filesystem::rename
- std::experimental::filesystem::resize_file
- std::experimental::filesystem::space
- std::experimental::filesystem::status
- std::experimental::filesystem::status_known
- std::experimental::filesystem::swap
- std::experimental::filesystem::symlink_status
- std::experimental::filesystem::system_complete
- std::experimental::filesystem::temp_directory_path
- std::experimental::filesystem::u8path
ms.openlocfilehash: f1b48ed6f533d4ccb5f9ef5e6dbcbd6e5cc4f7a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/14/2020
ms.locfileid: "81332052"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; 函数

[\<文件系统>](../standard-library/filesystem.md)标头中的这些自由函数对路径、文件、符号链接、目录和卷执行修改和查询操作。 有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="absolute"></a><a name="absolute"></a>绝对

```cpp
path absolute(const path& pval, const path& base = current_path());
```

函数返回与路径名相对对应于*pval*的绝对路径名称`base`：

1. 如果`pval.has_root_name() && pval.has_root_directory()`函数返回*pval*。

1. 如果`pval.has_root_name() && !pval.has_root_directory()``pval.root_name()` / `absolute(base).root_directory()`函数 / 返回`absolute(base).relative_path()`  / 。 `pval.relative_path()`

1. 如果`!pval.has_root_name() && pval.has_root_directory()`函数返回`absolute(base).root_name()` /  *pval*。

1. 如果`!pval.has_root_name() && !pval.has_root_directory()`函数返回`absolute(base)` /  *pval*。

## <a name="begin"></a><a name="begin"></a>开始

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

两个函数都返回*迭代器*。

## <a name="canonical"></a><a name="canonical"></a>规范

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

这些函数都形成一个绝对路径`pabs = absolute(pval, base)`名称（`pabs = absolute(pval)`或对于没有基本参数的重载），然后按照以下步骤将它简化为规范形式：

1. 其为`X`**true**的每个路径组件`is_symlink(X)`都替换为`read_symlink(X)`。

1. 将删除每个`.`路径组件（点是以前路径组件建立的当前目录）。

1. 将删除每对路径`X`/`..`组件（点点是以前路径组件建立的父目录）。

然后，函数返回`pabs`。

## <a name="copy"></a><a name="copy"></a>复制

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

这些函数都可能复制或链接一个或多个文件，*在从**到*控制*选择*，这被视为`copy_options::none`重载没有*选择*参数。 *选择*应最多包含一个：

- `skip_existing`、`overwrite_existing` 或 `update_existing`

- `copy_symlinks` 或 `skip_symlinks`

- `directories_only`、`create_symlinks` 或 `create_hard_links`

函数首先确定*从*`t`和`f`*到*file_status 的值。

- 如果`opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`，通过调用`symlink_status`

- 否则，通过调用`status`

- 否则报告错误。

如果`!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`，则它们报告错误（并且不执行任何其他操作）。

否则，如果`is_symlink(f)`这样：

- 如果`options & copy_options::skip_symlinks`，则不执行任何操作。

- 否则，如果`!exists(t)&& options & copy_options::copy_symlinks`，`copy_symlink(from, to, opts)`则 。

- 否则，报告错误。

否则，如果`is_regular_file(f)`、

- 如果`opts & copy_options::directories_only`，则不执行任何操作。

- 否则，如果`opts & copy_options::create_symlinks`，`create_symlink(to, from)`则 。

- 否则，如果`opts & copy_options::create_hard_links`，`create_hard_link(to, from)`则 。

- 否则，如果`is_directory(f)`，`copy_file(from, to` / `from.filename(), opts)`则 。

- 否则为 `copy_file(from, to, opts)`。

否则，如果`is_directory(f) && (opts & copy_options::recursive || !opts)`、

```cpp
if (!exists(t))
{  // copy directory contents recursively
    create_directory(to, from, ec);

    for (directory_iterator next(from), end; ec == error_code() && next != end; ++next)
    {
        copy(next->path(), to / next->path().filename(), opts, ec);
    }
}
```

否则，不执行任何操作。

## <a name="copy_file"></a><a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函数都可能*从**复制到**opts*控制下的文件，这被视为`copy_options::none`没有*opts*参数的重载。 *选项*最多应包含 的 1 `skip_existing` `overwrite_existing`，`update_existing`或 。

如果`exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`，则报告为该文件已存在的错误。

否则，如果`!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`，则尝试将文件的内容和属性*从*复制到 文件*到*。 如果复制尝试失败，则报告错误。

如果尝试复制并成功，则函数返回**true，** 否则**为 false**。

## <a name="copy_symlink"></a><a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

如果`is_directory(from)`， 函数`create_directory_symlink(from, to)`调用 。 否则，它将调用`create_symlink(from, to)`。

## <a name="create_directories"></a><a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

对于路径名称（如\/b\/c），函数根据需要创建目录 a\/和 b，以便它可以根据需要创建目录 b\/\/c。 仅当它实际上创建了目录*pval*时，它才返回**true。**

## <a name="create_directory"></a><a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

函数根据需要创建目录*pval。* 仅当它实际上创建了目录*pval*时，它才返回 true，在这种情况下，它复制现有文件*attr*的权限，`perms::all`或者使用没有*attr*参数的重载。

## <a name="create_directory_symlink"></a><a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

该函数创建链接作为指向*目录的*符号链接。

## <a name="create_hard_link"></a><a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

该函数创建链接作为指向 目录*或文件的硬*链接。

## <a name="create_symlink"></a><a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

该函数创建*链接*作为指向*文件的符号*链接。

## <a name="current_path"></a><a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

没有参数*pval*的函数返回当前目录的路径名称。 其余函数将当前目录设置为*pval*。

## <a name="end"></a><a name="end"></a>结束

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

第一个函数`directory_iterator()`返回，第二个函数返回`recursive_directory_iterator()`

## <a name="equivalent"></a><a name="equivalent"></a>等效

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

仅当*左侧*和*右侧*选择相同的文件系统实体时，函数才会返回**true。**

## <a name="exists"></a><a name="exists"></a>存在

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `status_known && stat.type() != file_not_found`。 第二个和第三个`exists(status(pval))`函数返回 。

## <a name="file_size"></a><a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

如果`exists(pval) && is_regular_file(pval)`和文件大小可以确定，则函数返回*pval*选择的文件的大小（以字节为单位）。 否则，它们会报告错误并`uintmax_t(-1)`返回 。

## <a name="hard_link_count"></a><a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

函数返回*pval*的硬链接数，如果\-发生错误，则返回 1。

## <a name="hash_value"></a><a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

函数返回 的`pval.native()`哈希值。

## <a name="is_block_file"></a><a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::block`。 其余函数返回`is_block_file(status(pval))`。

## <a name="is_character_file"></a><a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::character`。 其余函数返回`is_character_file(status(pval))`。

## <a name="is_directory"></a><a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::directory`。 其余函数返回`is_directory_file(status(pval))`。

## <a name="is_empty"></a><a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

如果`is_directory(pval)`，则 函数`directory_iterator(pval) == directory_iterator()`将返回 ;否则它返回`file_size(pval) == 0`。

## <a name="is_fifo"></a><a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::fifo`。 其余函数返回`is_fifo(status(pval))`。

## <a name="is_other"></a><a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::other`。 其余函数返回`is_other(status(pval))`。

## <a name="is_regular_file"></a><a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::regular`。 其余函数返回`is_regular_file(status(pval))`。

## <a name="is_socket"></a><a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::socket`。 其余函数返回`is_socket(status(pval))`。

## <a name="is_symlink"></a><a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::symlink`。 其余函数返回`is_symlink(status(pval))`。

## <a name="last_write_time"></a><a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

前两个函数返回*pval*的最后一次数据修改时间，`file_time_type(-1)`或者如果发生错误。 最后两个函数将*pval*的最后一次数据修改时间设置为*new_time*。

## <a name="permissions"></a><a name="permissions"></a>权限

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

这些函数将*pval*选择的路径名称的权限设置为`mask & perms::mask`受 控制的`perms & (perms::add_perms | perms::remove_perms)`。 *掩码*最多应包含和`perms::add_perms`。 `perms::remove_perms`

如果`mask & perms::add_perms`，则函数将权限设置为`status(pval).permissions() | mask & perms::mask`。 否则，如果`mask & perms::remove_perms`、函数将权限设置为`status(pval).permissions() & ~(mask & perms::mask)`。 否则，函数将权限设置为`mask & perms::mask`。

## <a name="proximate"></a><a name="proximate"></a>近似

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a><a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

这些函数报告错误，如果`path()`返回`!is_symlink(pval)`。 否则，函数返回包含符号链接的 `path` 类型的对象。

## <a name="relative"></a><a name="relative"></a>相对

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a><a name="remove"></a>删除

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

仅当已成功删除文件时`exists(symlink_status(pval))`，函数才会返回**true。** 符号链接本身被删除，而不是它选择的文件。

## <a name="remove_all"></a><a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

如果*pval*是目录，则函数递归地删除所有目录条目，然后删除条目本身。 否则，函数将调用`remove`。 它们返回已成功删除的所有元素数。

## <a name="rename"></a><a name="rename"></a>重 命名

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

函数*从*重命名*到*。 符号链接本身被重命名，而不是它选择的文件。

## <a name="resize_file"></a><a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

函数更改文件的大小，以便`file_size(pval) == size`

## <a name="space"></a><a name="space"></a>空间

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

函数返回有关*pval*选择的卷的信息，在 类型 的结构`space_info`中。 结构包含`uintmax_t(-1)`任何无法确定的值。

## <a name="status"></a><a name="status"></a>地位

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

函数返回与*pval*关联的路径名状态、文件类型和权限。 符号链接本身未测试，但会测试它选择的文件。

## <a name="status_known"></a><a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

函数返回`stat.type() != file_type::none`

## <a name="swap"></a><a name="swap"></a>交换

```cpp
void swap(path& left, path& right) noexcept;
```

函数交换*左右**的内容。*

## <a name="symlink_status"></a><a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

函数返回与*pval*关联的路径名称符号链接状态、文件类型和权限。 函数的运行情况与`status(pval)`symlink 本身测试不同，而不是它选择的文件。

## <a name="system_complete"></a><a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

这些函数返回纳入考虑的绝对路径名，并在必要时返回与其根名称关联的当前目录。 \(对于 POSIX，函数返回`absolute(pval)`。\)

## <a name="temp_directory_path"></a><a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

这些函数返回适合包含临时文件的目录的路径名。

## <a name="u8path"></a><a name="u8path"></a>u8路径

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

第一个函数的表示与`path(source)`第二个函数相同的，`path(first, last)`除了每个情况下所选的源被视为编码为 UTF-8 的字符元素序列，无论文件系统是什么。

## <a name="weakly_canonical"></a><a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
