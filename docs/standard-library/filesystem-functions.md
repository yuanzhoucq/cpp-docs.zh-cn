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
ms.openlocfilehash: 1ab57a6fc13a03d02963f3d7ecc80f63decb9487
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 03/16/2020
ms.locfileid: "79427109"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; 函数

[\<filesystem >](../standard-library/filesystem.md)标头中的这些自由功能对路径、文件、符号链接、目录和卷执行修改和查询操作。 有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="absolute"></a>绝

```cpp
path absolute(const path& pval, const path& base = current_path());
```

该函数返回相对于 pathname `base`的相对于*pval*的绝对路径名：

1. 如果 `pval.has_root_name() && pval.has_root_directory()` 则函数返回*pval*。

1. 如果 `pval.has_root_name() && !pval.has_root_directory()` 该函数将返回 `pval.root_name()` / `absolute(base).root_directory()` / `absolute(base).relative_path()` / `pval.relative_path()`。

1. 如果 `!pval.has_root_name() && pval.has_root_directory()` 该函数将返回 `absolute(base).root_name()` / *pval*。

1. 如果 `!pval.has_root_name() && !pval.has_root_directory()` 该函数将返回 `absolute(base)` / *pval*。

## <a name="begin"></a>准备

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

这两个函数都返回*iter*。

## <a name="canonical"></a>规范

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

函数全部形成绝对路径名 `pabs = absolute(pval, base)` （对于没有基参数的重载，则使用 `pabs = absolute(pval)`），然后将其缩小为以下一系列步骤中的规范格式：

1. `is_symlink(X)` 为**true** `X` 的每个路径组件都将被 `read_symlink(X)`替换。

1. 将删除每个路径组件 `.` （点是由以前的路径组件建立的当前目录）。

1. 将删除每对路径组件 `X`/`..` （点点是由以前的路径组件建立的父目录）。

然后，该函数返回 `pabs`。

## <a name="copy"></a>复本

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函数可以*从*到的控件中将一个或多个文件复制或*链接到*`copy_options::none` *，然后在 "* " 只包含以下项之一：

- `skip_existing`、`overwrite_existing` 或 `update_existing`

- `copy_symlinks` 或 `skip_symlinks`

- `directories_only`、`create_symlinks` 或 `create_hard_links`

函数首先确定 *`f` 的 file_status*值 *，并将 `t` 为：*

- 如果 `opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`，则调用 `symlink_status`

- 否则，通过调用 `status`

- 否则报告错误。

如果 `!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`，则它们将报告一个错误（不执行任何其他操作）。

否则，如果 `is_symlink(f)`，则：

- 如果 `options & copy_options::skip_symlinks`，则不执行任何操作。

- 否则，如果 `!exists(t)&& options & copy_options::copy_symlinks`，`copy_symlink(from, to, opts)`。

- 否则，将报告错误。

否则，如果 `is_regular_file(f)`，则：

- 如果 `opts & copy_options::directories_only`，则不执行任何操作。

- 否则，如果 `opts & copy_options::create_symlinks`，`create_symlink(to, from)`。

- 否则，如果 `opts & copy_options::create_hard_links`，`create_hard_link(to, from)`。

- 否则，如果 `is_directory(f)`，则 `copy_file(from, to` / `from.filename(), opts)`。

- 否则为 `copy_file(from, to, opts)`。

否则，如果 `is_directory(f) && (opts & copy_options::recursive || !opts)`，则：

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

## <a name="copy_file"></a>copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

所有函数都可能将文件*从中*的 "从"*复制到 ""，* *而不是*"查找"*参数，该*函数将作为重载的 `copy_options::none`。 只包含一个 `skip_existing`、`overwrite_existing`或 `update_existing`。

如果 `exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`，则报告为错误，指出该文件已存在。

否则，如果 `!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`，则尝试将文件的内容和属性*从* *复制到文件。* 如果复制尝试失败，则报告错误。

如果尝试复制并成功，则函数返回**true** ，否则返回**false**。

## <a name="copy_symlink"></a>copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

如果 `is_directory(from)`，则该函数将调用 `create_directory_symlink(from, to)`。 否则，它会调用 `create_symlink(from, to)`。

## <a name="create_directories"></a>create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

对于诸如\/b\/c 的路径名，函数根据需要创建目录 a 和\/b，以便它可以根据需要创建\/b\/c 目录。 仅当它实际创建目录*pval*时，它才返回**true** 。

## <a name="create_directory"></a>create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

函数根据需要创建目录*pval* 。 仅当它实际创建目录*pval*时，它才返回 true，在这种情况*下，它*将从现有的文件属性复制权限，或对没有*attr*参数的重载使用 `perms::all`。

## <a name="create_directory_symlink"></a>create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

函数将链接创建为*指向目录的*符号链接。

## <a name="create_hard_link"></a>create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

函数将链接创建为指向目录*或文件的*硬链接。

## <a name="create_symlink"></a>create_symlink

```cpp
void create_symlink(const path& to, const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

函数将链接创建为*指向文件的* *链接*。

## <a name="current_path"></a>current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

没有参数*pval*的函数将返回当前目录的路径名。 其余函数将当前目录设置为*pval*。

## <a name="end"></a>end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

第一个函数返回 `directory_iterator()`，第二个函数返回 `recursive_directory_iterator()`

## <a name="equivalent"></a>项

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

仅当*向左*和*向右*选择相同的文件系统实体时，函数才返回**true** 。

## <a name="exists"></a>  exists

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `status_known && stat.type() != file_not_found`。 第二个和第三个函数返回 `exists(status(pval))`。

## <a name="file_size"></a>file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

如果 `exists(pval) && is_regular_file(pval)`，则函数返回由*pval*选择的文件的大小（以字节为单位），并且可以确定文件大小。 否则，它们会报告错误并返回 `uintmax_t(-1)`。

## <a name="hard_link_count"></a>hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

该函数返回*pval*的硬链接数，如果发生错误，则返回 \-1。

## <a name="hash_value"></a>hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

函数返回 `pval.native()`的哈希值。

## <a name="is_block_file"></a>is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::block`。 其余函数返回 `is_block_file(status(pval))`。

## <a name="is_character_file"></a>is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::character`。 其余函数返回 `is_character_file(status(pval))`。

## <a name="is_directory"></a>is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::directory`。 其余函数返回 `is_directory_file(status(pval))`。

## <a name="is_empty"></a>is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

如果 `is_directory(pval)`，则函数返回 `directory_iterator(pval) == directory_iterator()`;否则，它将返回 `file_size(pval) == 0`。

## <a name="is_fifo"></a>is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::fifo`。 其余函数返回 `is_fifo(status(pval))`。

## <a name="is_other"></a>is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::other`。 其余函数返回 `is_other(status(pval))`。

## <a name="is_regular_file"></a>is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::regular`。 其余函数返回 `is_regular_file(status(pval))`。

## <a name="is_socket"></a>is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::socket`。 其余函数返回 `is_socket(status(pval))`。

## <a name="is_symlink"></a>is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::symlink`。 其余函数返回 `is_symlink(status(pval))`。

## <a name="last_write_time"></a>last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

前两个函数返回*pval*的上次数据修改时间，如果发生错误，则返回 `file_time_type(-1)`。 最后两个函数将*pval*的上次数据修改时间设置为*new_time*。

## <a name="permissions"></a>访问

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

函数将*pval*选择的路径名的权限设置为在 `perms & (perms::add_perms | perms::remove_perms)`控制下 `mask & perms::mask`。 *掩码*应最多包含 `perms::add_perms` 和 `perms::remove_perms`中的一个。

如果 `mask & perms::add_perms`，则这些函数将权限设置为 `status(pval).permissions() | mask & perms::mask`。 否则，如果 `mask & perms::remove_perms`，这些函数将权限设置为 `status(pval).permissions() & ~(mask & perms::mask)`。 否则，这些函数将权限设置为 `mask & perms::mask`。

## <a name="proximate"></a>近程

```cpp
path proximate(const path& p, error_code& ec);
path proximate(const path& p, const path& base = current_path());
path proximate(const path& p, const path& base, error_code& ec);
```

## <a name="read_symlink"></a>read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

函数报告错误并返回 `path()` 如果 `!is_symlink(pval)`。 否则，函数返回包含符号链接的 `path` 类型的对象。

## <a name="relative"></a>相对

```cpp
path relative(const path& p, error_code& ec);
path relative(const path& p, const path& base = current_path());
path relative(const path& p, const path& base, error_code& ec);
```

## <a name="remove"></a>取消

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

仅当 `exists(symlink_status(pval))` 和文件成功删除时，函数才返回**true** 。 符号链接本身会被删除，而不是它所选择的文件。

## <a name="remove_all"></a>remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

如果*pval*是一个目录，则函数将以递归方式删除所有目录项，然后删除该项本身。 否则，这些函数将调用 `remove`。 它们返回已成功删除的所有元素数。

## <a name="rename"></a>重命名

```cpp
void rename(const path& from, const path& to);
void rename(const path& from, const path& to, error_code& ec) noexcept;
```

函数将*从*重命名*为。* 符号链接自行重命名，而不是它所选择的文件。

## <a name="resize_file"></a>resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

函数会更改文件的大小，以便 `file_size(pval) == size`

## <a name="space"></a>空间

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

函数在 `space_info`类型的结构中返回有关*pval*选择的卷的信息。 结构包含不能确定的任何值的 `uintmax_t(-1)`。

## <a name="status"></a>状态值

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

这些函数返回与*pval*关联的路径名状态、文件类型和权限。 符号链接本身并未经过测试，而是它所选择的文件。

## <a name="status_known"></a>status_known

```cpp
bool status_known(file_status stat) noexcept;
```

函数返回 `stat.type() != file_type::none`

## <a name="swap"></a>购

```cpp
void swap(path& left, path& right) noexcept;
```

函数将交换*左侧*和*右侧*的内容。

## <a name="symlink_status"></a>symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

这些函数返回与*pval*关联的路径名符号链接状态、文件类型和权限。 函数与 `status(pval)` 的行为相同，不同之处在于符号符号本身经过测试，而不是它所选择的文件。

## <a name="system_complete"></a>system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

这些函数返回纳入考虑的绝对路径名，并在必要时返回与其根名称关联的当前目录。 \(POSIX，函数返回 `absolute(pval)`。\)

## <a name="temp_directory_path"></a>temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

这些函数返回适合包含临时文件的目录的路径名。

## <a name="u8path"></a>u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

第一个函数的行为与 `path(source)` 相同，第二个函数的行为与 `path(first, last)` 相同，不同之处在于，每个事例中的所选源将作为编码为 UTF-8 的 char 元素序列，无论是什么文件系统。

## <a name="weakly_canonical"></a>weakly_canonical

```cpp
path weakly_canonical(const path& p);
path weakly_canonical(const path& p, error_code& ec);
```
