---
title: '&lt;filesystem&gt;'
description: 描述标准C++库的 filesystem 标头中的类、函数和类型。
ms.date: 01/22/2020
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: dbe6dc89d5460a08ffafd86aa3fcd01222c82166
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725677"
---
# &lt;filesystem&gt;

包括标头 &lt;filesystem> 访问操作和检索有关路径、文件和目录的信息的类和函数。

## <a name="syntax"></a>语法

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> 在 Visual Studio 2017 版本中，\<filesystem> 标头尚不是C++标准的。 C++在 Visual Studio 2017 中，RTW 实现了最终草案标准，可在[ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)中找到。 Visual Studio 2017 版本15.7 及更高版本支持新的 c + + 17 \<filesystem> standard。
> 这是一个全新的实现，与上一个 `std::experimental` 版本不兼容。 这是必要的，如符号支持、bug 修复和标准要求的行为更改。 目前，包括 \<filesystem> 提供了新的 `std::filesystem` 和之前的 `std::experimental::filesystem`。 包括 \<experimental/filesystem> 仅提供旧 experimental 实现。 此 experimental 实现将在下一次 ABI 中断版本的库中删除。

此标头支持两大类主机操作系统（Microsoft Windows 和 POSIX）之一的文件系统。

虽然这两种操作系统的大多数功能均相同，但本文档将介绍它们之间存在的差异。 例如：

- Windows 支持多个根名称，例如 `c:` 或 `\\network_name`。 文件系统由一林林组成，每个树都有其自己的根目录（例如 `c:\` 或 `\\network_name\`），每个树都有其自己的当前目录，用于完成相对路径名（不是绝对路径名）。

- POSIX 支持单个树，无根名称、单个根目录 `/`和单个当前目录。

另一个重要差异是路径名的本机表示方式：

- Windows 使用以 null 结尾的 **wchar_t** 序列，编码为 utf-16 （每个字符一个或多个元素）。

- POSIX 使用以 null 结尾的 **char** 序列，编码为 utf-8 （每个字符一个或多个元素）。

- 类的对象 `path` 以本机形式存储路径名，但支持在此存储的窗体和多个外部窗体之间轻松转换：

  - **char** 的以 null 结尾的序列，编码为操作系统的优先。

  - 以 null 结尾的 **char** 序列，编码为 utf-8。

  - **wchar_t** 的以 null 结尾的序列，编码为操作系统的优先。

  - 以 null 结尾的 **char16_t** 序列，编码为 utf-16。

  - 以 null 结尾的 **char32_t** 序列，编码为32。

  通过使用一个或多个 `codecvt` facet，按需调节这些表示形式之间的相互转换。 如果未指定特定的区域设置对象，则将从全局区域设置获取这些 facet。

另一个差别是每个操作系统允许你用于指定文件或目录访问权限的详细信息：

- Windows 记录文件是只读还是可写，这对于目录没有意义。

- POSIX 记录文件是否可以读取、写入或执行（如果是目录，则扫描）。 和，无论是允许所有者、所有者组还是每个人操作，还有其他一些权限。

两个系统的共同点是通过根名称后施加于路径名的结构。 对于路径名 `c:/abc/xyz/def.ext`：

- 根名称为 `c:`。

- `/`根目录。

- 根路径是 `c:/`。

- 相对路径是 `abc/xyz/def.ext`。

- 父路径为 `c:/abc/xyz`。

- 文件名为 `def.ext`。

- 主体 `def`。

- 扩展是 `.ext`的。

一个次要差别是路径名中目录序列之间的首选分隔符。 这两个操作系统都允许写入正斜杠 `/`，但在某些上下文中，Windows 更喜欢反斜杠 `\`。 实现将其首选分隔符存储在 `path`的数据成员 `preferred_separator` 中。

最后，`path` 对象具有一项重要功能：在标头[\<m >](fstream.md)中定义的类中，可以在任何位置使用 filename 参数。

有关详细信息和代码示例，请参阅[文件系统导航C++（）](../standard-library/file-system-navigation.md)。

## <a name="members"></a>Members

### <a name="classes"></a>类

|||
|-|-|
|[directory_entry 类](../standard-library/directory-entry-class.md)|描述一个对象，该对象由 `directory_iterator` 或 `recursive_directory_iterator` 返回，并包含 `path`。|
|[directory_iterator 类](../standard-library/directory-iterator-class.md)|描述通过文件系统目录中的文件名排序的输入迭代器。|
|[filesystem_error 类](../standard-library/filesystem-error-class.md)|所引发以报告低级系统溢出的异常的基类。|
|[path 类](../standard-library/path-class.md)|定义一个类，该类存储适合用作文件名的模板类型 `String` 的对象。|
|[recursive_directory_iterator 类](../standard-library/recursive-directory-iterator-class.md)|描述通过文件系统目录中的文件名排序的输入迭代器。 迭代器还可以降到子目录中。|
|[file_status 类](../standard-library/file-status-class.md)|包装 `file_type`。|

### <a name="structs"></a>结构

|||
|-|-|
|[space_info 结构](../standard-library/space-info-structure.md)|保存有关卷的信息。|

## <a name="functions"></a>函数

[\<filesystem> 函数](../standard-library/filesystem-functions.md)

## <a name="operators"></a>运算符

[\<filesystem> 运算符](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>枚举

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|如果目标文件已存在，则与 [copy_file](../standard-library/filesystem-functions.md#copy_file) 一起使用的枚举将决定行为。|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|为目录迭代器指定选项的枚举。|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|文件类型的枚举。|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| 枚举 `permissions` 函数的选项。 |
|[perms](../standard-library/filesystem-enumerations.md#perms)|用于传达权限和权限选项的位掩码类型|

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)
