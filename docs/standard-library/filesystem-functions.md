---
title: '&lt;filesystem&gt; 函数 | Microsoft 文档'
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
ms.assetid: be3cb821-4728-4d47-ab78-858fa8aa5045
author: corob-msft
ms.author: corob
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
ms.workload:
- cplusplus
ms.openlocfilehash: 4dc53bff438830cfb8a7b0414c4e5cfb111f8f31
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691492"
---
# <a name="ltfilesystemgt-functions"></a>&lt;filesystem&gt; 函数

[\<filesystem>](../standard-library/filesystem.md) 标头中的这些自由格式函数对路径、文件、符号链接、目录和卷执行修改和查询操作。 有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。
||||
|-|-|-|
|[absolute](#absolute)|[begin](#begin)|[规范](#canonical)|
|[copy](#copy)|[copy_file](#copy_file)|[copy_symlink](#copy_symlink)|
|[create_directories](#create_directories)|[create_directory](#create_directory)|[create_directory_symlink](#create_directory_symlink)|
|[create_hard_link](#create_hard_link)|[create_symlink](#create_symlink)|[current_path](#current_path)|
|[end](#end)|[equivalent](#equivalent)|[exists](#exists)|
|[file_size](#file_size)|[hard_link_count](#hard_link_count)|[hash_value](#hash_value)|
|[is_block_file](#is_block_file)|[is_character_file](#is_character_file)|[is_directory](#is_directory)|
|[is_empty](#is_empty)|[is_fifo](#is_fifo)|[is_other](#is_other)|
|[is_regular_file](#is_regular_file)|[is_socket](#is_socket)|[is_symlink](#is_symlink)|
|[last_write_time](#last_write_time)|[permissions](#permissions)|[read_symlink](#read_symlink)|
|[remove](#remove)|[remove_all](#remove_all)|[rename](#rename)|
|[resize_file](#resize_file)|[space](#space)|[status](#status)|
|[status_known](#status_known)|[swap](#swap)|[symlink_status](#symlink_status)|
|[system_complete](#system_complete)|[temp_directory_path](#temp_directory_path)|[u8path](#u8path)|


## <a name="absolute"></a> 绝对

```cpp
path absolute(const path& pval, const path& base = current_path());
```

该函数将返回对应的绝对路径名*pval*相对于路径名`base`:

1. 如果`pval.has_root_name() && pval.has_root_directory()`函数将返回*pval*。

1. 如果`pval.has_root_name() && !pval.has_root_directory()`函数将返回`pval.root_name()`  /  `absolute(base).root_directory()`  /  `absolute(base).relative_path()`  /  `pval.relative_path()`。

1. 如果`!pval.has_root_name() && pval.has_root_directory()`函数将返回`absolute(base).root_name()`  /  *pval*。

1. 如果`!pval.has_root_name() && !pval.has_root_directory()`函数将返回`absolute(base)`  /  *pval*。

## <a name="begin"></a>  begin

```cpp
const directory_iterator& begin(const directory_iterator& iter) noexcept;
const recursive_directory_iterator&
    begin(const recursive_directory_iterator& iter) noexcept;
```

这两个函数返回*iter*。

## <a name="canonical"></a>  规范

```cpp
path canonical(const path& pval, const path& base = current_path());
path canonical(const path& pval, error_code& ec);
path canonical(const path& pval, const path& base, error_code& ec);
```

这些函数均形成绝对路径名`pabs = absolute(pval, base)`(或`pabs = absolute(pval)`使用任何基本参数的重载)，然后将其减少到规范格式按以下顺序的步骤：

1. 每个路径组件`X`为其`is_symlink(X)`是**true**替换为`read_symlink(X)`。

1. 每个路径组件`.`（圆点是由以前的路径组件建立的当前目录） 中删除。

1. 每个对路径组件`X` / `..` （双园点是由以前的路径组件建立的父目录） 中删除。

然后，该函数返回`pabs`。

## <a name="copy"></a>  copy

```cpp
void copy(const path& from, const path& to);
void copy(const path& from, const path& to, error_code& ec) noexcept;
void copy(const path& from, const path& to, copy_options opts);
void copy(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

这些函数都可能复制或链接处的一个或多个文件*从*到*到*的控制下*opts*，这被视为`copy_options::none`没有的重载*opts*参数。 *opts*应最多包含：

- `skip_existing`、`overwrite_existing` 或 `update_existing`

- `copy_symlinks` 或 `skip_symlinks`

- `directories_only`、`create_symlinks` 或 `create_hard_links`

函数首先确定 file_status 值`f`有关*从*并`t`有关*到*:

- 如果`opts & (copy_options::create_symlinks | copy_options::skip_symlinks)`，通过调用 `symlink_status`

- 否则为通过调用 `status`

- 否则报告错误。

如果`!exists(f) || equivalent(f, t) || is_other(f) || is_other(t) || is_directory(f)&& is_regular_file(t)`，它们然后报告错误 （并不执行任何其他操作）。

否则为如果`is_symlink(f)`然后：

- 如果`options & copy_options::skip_symlinks`然后不执行任何操作。

- 否则为如果`!exists(t)&& options & copy_options::copy_symlinks`然后`copy_symlink(from, to, opts)`。

- 否则报告错误。

否则为如果`is_regular_file(f)`然后：

- 如果`opts & copy_options::directories_only`然后不执行任何操作。

- 否则为如果`opts & copy_options::create_symlinks`然后`create_symlink(to, from)`。

- 否则为如果`opts & copy_options::create_hard_links`然后`create_hard_link(to, from)`。

- 否则为如果`is_directory(f)`然后`copy_file(from, to`  /  `from.filename(), opts)`。

- 否则为 `copy_file(from, to, opts)`。

否则为如果`is_directory(f) && (opts & copy_options::recursive || !opts)`然后：

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

## <a name="copy_file"></a>  copy_file

```cpp
bool copy_file(const path& from, const path& to);
bool copy_file(const path& from, const path& to, error_code& ec) noexcept;
bool copy_file(const path& from, const path& to, copy_options opts);
bool copy_file(const path& from, const path& to, copy_options opts, error_code& ec) noexcept;
```

函数都可能处的文件复制*从*到*到*的控制下*opts*，其结果作为`copy_options::none`没有重载*opts*参数。 *opts*应最多包含`skip_existing`， `overwrite_existing`，或`update_existing`。

如果`exists(to) && !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options::update_existing))`则报告一个错误，该文件已存在。

否则为如果`!exists(to) || opts & copy_options::overwrite_existing || opts & copy_options::update_existing&& last_write_time(to) < last_write_time(from) || !(opts & (copy_options::skip_existing | copy_options::overwrite_existing | copy_options:update_existing))`然后尝试将复制的内容和文件的属性*从*的文件*到*。 如果复制尝试失败，则报告错误。

这些函数返回 **，则返回 true**如果尝试复制并成功，否则**false**。

## <a name="copy_symlink "></a>  copy_symlink

```cpp
void copy_symlink(const path& from, const path& to);
void copy_symlink(const path& from, const path& to, error_code& ec) noexcept;
```

如果`is_directory(from)`函数调用`create_directory_symlink(from, to)`。 否则，它会调用`create_symlink(from, to)`。

## <a name="create_directories"></a>  create_directories

```cpp
bool create_directories(const path& pval);
bool create_directories(const path& pval, error_code& ec) noexcept;
```

对于如 a\/b\/c 这样的路径名，函数根据需要创建目录 a 和 a\/b，以便它可以根据需要创建目录 a\/b\/c。 它将返回 **，则返回 true**仅当它实际创建目录*pval*。

## <a name="create_directory"></a>  create_directory

```cpp
bool create_directory(const path& pval);

bool create_directory(const path& pval, error_code& ec) noexcept;
bool create_directory(const path& pval, const path& attr);
bool create_directory(const path& pval, const path& attr, error_code& ec) noexcept;
```

该函数将创建该目录*pval*根据需要。 它返回 true 仅当它实际创建目录*pval*，在这种情况下它将权限从现有的文件*attr*，或使用`perms::all`没有重载*attr*参数。

## <a name="create_directory_symlink "></a>  create_directory_symlink

```cpp
void create_directory_symlink(const path& to, const path& link);
void create_directory_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

该函数将链接创建为指向目录*到*。

## <a name="create_hard_link"></a>  create_hard_link

```cpp
void create_hard_link(const path& to,  const path& link);
void create_hard_link(const path& to, const path& link, error_code& ec) noexcept;
```

该函数将链接创建为指向目录或文件的硬链接*到*。

## <a name="create_symlink "></a>  create_symlink

```cpp
void create_symlink(const path& to,  const path& link);

void create_symlink(const path& to, const path& link, error_code& ec) noexcept;
```

该函数将创建*链接*作为该文件的符号链接*到*。

## <a name="current_path"></a>  current_path

```cpp
path current_path();
path current_path(error_code& ec);
void current_path(const path& pval);
void current_path(const path& pval, error_code& ec) noexcept;
```

不使用任何参数的函数*pval*返回当前目录的路径名。 其余函数将当前目录设置为*pval*。

## <a name="end"></a>  end

```cpp
directory_iterator& end(const directory_iterator& iter) noexcept;
recursive_directory_iterator& end(const recursive_directory_iterator& iter) noexcept;
```

第一个函数返回`directory_iterator()`和第二个函数返回 `recursive_directory_iterator()`

## <a name="equivalent"></a>  equivalent

```cpp
bool equivalent(const path& left, const path& right);
bool equivalent(const path& left, const path& right, error_code& ec) noexcept;
```

这些函数返回 **，则返回 true**仅当*左*并*右*指定相同的文件系统实体。

## <a name="exists"></a>  exists

```cpp
bool exists(file_status stat) noexcept;
bool exists(const path& pval);
bool exists(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `status_known && stat.type() != file_not_found`。 第二个和第三个函数返回`exists(status(pval))`。

## <a name="file_size"></a>  file_size

```cpp
uintmax_t file_size(const path& pval);
uintmax_t file_size(const path& pval, error_code& ec) noexcept;
```

这些函数返回以字节为单位指定的文件的大小*pval*，如果`exists(pval) && is_regular_file(pval)`，可以确定文件大小。 否则为报告错误并返回`uintmax_t(-1)`。

## <a name="hard_link_count"></a>  hard_link_count

```cpp
uintmax_t hard_link_count(const path& pval);
uintmax_t hard_link_count(const path& pval, error_code& ec) noexcept;
```

该函数返回的硬链接数*pval*，或\-1; 如果发生错误。

## <a name="hash_value"></a>  hash_value

```cpp
size_t hash_value(const path& pval) noexcept;
```

该函数返回的哈希值`pval.native()`。

## <a name="is_block_file"></a>  is_block_file

```cpp
bool is_block_file(file_status stat) noexcept;
bool is_block_file(const path& pval);
bool is_block_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::block`。 其余函数返回`is_block_file(status(pval))`。

## <a name="is_character_file"></a>  is_character_file

```cpp
bool is_character_file(file_status stat) noexcept;
bool is_character_file(const path& pval);
bool is_character_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::character`。 其余函数返回`is_character_file(status(pval))`。

## <a name="is_directory "></a>  is_directory

```cpp
bool is_directory(file_status stat) noexcept;
bool is_directory(const path& pval);
bool is_directory(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::directory`。 其余函数返回`is_directory_file(status(pval))`。

## <a name="is_empty"></a>  is_empty

```cpp
bool is_empty(file_status stat) noexcept;
bool is_empty(const path& pval);
bool is_empty(const path& pval, error_code& ec) noexcept;
```

如果`is_directory(pval)`函数将返回`directory_iterator(pval) == directory_iterator()`; 否则它将返回`file_size(pval) == 0`。

## <a name="is_fifo"></a>  is_fifo

```cpp
bool is_fifo(file_status stat) noexcept;
bool is_fifo(const path& pval);
bool is_fifo(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::fifo`。 其余函数返回`is_fifo(status(pval))`。

## <a name="is_other"></a>  is_other

```cpp
bool is_other(file_status stat) noexcept;
bool is_other(const path& pval);
bool is_other(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::other`。 其余函数返回`is_other(status(pval))`。

## <a name="s_regular_file"></a>  is_regular_file

```cpp
bool is_regular_file(file_status stat) noexcept;
bool is_regular_file(const path& pval);
bool is_regular_file(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::regular`。 其余函数返回`is_regular_file(status(pval))`。

## <a name="is_socket"></a>  is_socket

```cpp
bool is_socket(file_status stat) noexcept;
bool is_socket(const path& pval);
bool is_socket(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::socket`。 其余函数返回`is_socket(status(pval))`。

## <a name="is_symlink"></a>  is_symlink

```cpp
bool is_symlink(file_status stat) noexcept;
bool is_symlink(const path& pval);
bool is_symlink(const path& pval, error_code& ec) noexcept;
```

第一个函数返回 `stat.type() == file_type::symlink`。 其余函数返回`is_symlink(status(pval))`。

## <a name="last_write_time"></a>  last_write_time

```cpp
file_time_type last_write_time(const path& pval);
file_time_type last_write_time(const path& pval, error_code& ec) noexcept;
void last_write_time(const path& pval, file_time_type new_time);
void last_write_time(const path& pval, file_time_type new_time, error_code& ec) noexcept;
```

前两个函数返回的上次数据修改时间*pval*，或`file_time_type(-1)`如果发生错误。 最后两个函数将设置的最后一个数据修改时间*pval*到*new_time*。

## <a name="permissions"></a>  permissions

```cpp
void permissions(const path& pval, perms mask);
void permissions(const path& pval, perms mask, error_code& ec) noexcept;
```

这些函数将设置为指定的路径名的权限*pval*到`mask & perms::mask`的控制下`perms & (perms::add_perms | perms::remove_perms)`。 *掩码*应最多包含`perms::add_perms`和`perms::remove_perms`。

如果`mask & perms::add_perms`函数将权限设置为`status(pval).permissions() | mask & perms::mask`。 否则为如果`mask & perms::remove_perms`函数将权限设置为`status(pval).permissions() & ~(mask & perms::mask)`。 否则，函数将权限设置为`mask & perms::mask`。

## <a name="read_symlink"></a>  read_symlink

```cpp
path read_symlink(const path& pval);
path read_symlink(const path& pval, error_code& ec);
```

函数报告错误并返回`path()`如果`!is_symlink(pval)`。 否则，函数返回包含符号链接的 `path` 类型的对象。

## <a name="remove"></a>  remove

```cpp
bool remove(const path& pval);
bool remove(const path& pval, error_code& ec) noexcept;
```

这些函数返回 **，则返回 true**仅当`exists(symlink_status(pval))`并且文件已成功删除。 符号链接自行删除，无需它指定的文件。

## <a name="remove_all"></a>  remove_all

```cpp
uintmax_t remove_all(const path& pval);
uintmax_t remove_all(const path& pval, error_code& ec) noexcept;
```

如果*pval*是一个目录，函数以递归方式删除所有目录项，则该项本身。 否则，函数调用`remove`。 它们返回已成功删除的所有元素数。

## <a name="rename"></a>  rename

```cpp
void rename(const path& from,  const path& to);
void rename(const path& from,  const path& to, error_code& ec) noexcept;
```

函数重命名*从*到*到*。 符号链接自行重命名，无需它指定的文件。

## <a name="resize_file"></a>  resize_file

```cpp
void resize(const path& pval, uintmax_t size);
void resize(const path& pval, uintmax_t size, error_code& ec) noexcept;
```

函数更改文件的大小，以便 `file_size(pval) == size`

## <a name="space"></a>  space

```cpp
space_info space(const path& pval);
space_info space(const path& pval, error_code& ec) noexcept;
```

该函数返回有关指定的卷的信息*pval*，在类型的结构`space_info`。 该结构包含`uintmax_t(-1)`无法确定任何值。

## <a name="status"></a>  status

```cpp
file_status status(const path& pval);
file_status status(const path& pval, error_code& ec) noexcept;
```

这些函数返回的路径名状态、 文件类型和关联的权限*pval*。 符号链接不自行测试，而是对它指定的文件进行测试。

## <a name="status_known"></a>  status_known

```cpp
bool status_known(file_status stat) noexcept;
```

该函数将返回 `stat.type() != file_type::none`

## <a name="swap"></a>  swap

```cpp
void swap(path& left, path& right) noexcept;
```

该函数交换的内容*左*并*右*。

## <a name="symlink_status"></a>  symlink_status

```cpp
file_status symlink_status(const path& pval);
file_status symlink_status(const path& pval, erroxr_code& ec) noexcept;
```

这些函数返回的路径名符号链接状态、 文件类型和关联的权限*pval*。 这些函数的行为相同`status(pval)`唯一的差别在于符号链接自行测试，不它指定的文件。

## <a name="system_complete"></a>  system_complete

```cpp
path system_complete(const path& pval);
path system_complete(const path& pval, error_code& ec);
```

这些函数返回纳入考虑的绝对路径名，并在必要时返回与其根名称关联的当前目录。 \(对于 Posix，这些函数返回`absolute(pval)`。\)

## <a name="temp_directory_path"></a>  temp_directory_path

```cpp
path temp_directory_path();
path temp_directory_path(error_code& ec);
```

这些函数返回适合包含临时文件的目录的路径名。

## <a name="u8path"></a>  u8path

```cpp
template <class Source>
path u8path(const Source& source);

template <class InIt>
path u8path(InIt first, InIt last);
```

第一个函数的行为相同`path(source)`和第二个函数的行为相同`path(first, last)`只不过每个用例中的指定的源被视为编码为 utf-8，而不考虑文件系统的 char 元素序列。
