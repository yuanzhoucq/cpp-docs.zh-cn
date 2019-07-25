---
title: '&lt;filesystem&gt;'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
ms.openlocfilehash: 6f97ad75dcf3f01406f305b713b9d14cbe527c52
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457023"
---
# <a name="ltfilesystemgt"></a>&lt;filesystem&gt;

包含标头 &lt;filesystem>，用于访问操作和检索有关路径、文件和目录的信息的类和函数。

## <a name="syntax"></a>语法

```cpp
#include <experimental/filesystem> // C++-standard header file name
#include <filesystem> // Microsoft-specific implementation header file name
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> 在 Visual Studio 2017 版本中, \<filesystem > 标头尚不是C++标准版本。 C++在 Visual Studio 2017 (MSVC v141) 中, 可实现在[ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)中找到的最终草案标准。

此标头支持两大种类的主机操作系统之一的文件系统:Microsoft Windows 和 Posix。

虽然这两种操作系统的大多数功能均相同，但本文档将介绍它们之间存在的差异。 例如：

- Windows 支持多个根名称，例如 c: 或 \\\network_name。 文件系统由树林组成，每个树都有其自己的根目录（例如 c:\ 或 \\\\network_name\\），且每个树都有其自己的当前目录，用于完善相对路径名（非绝对路径名）。

- Posix 支持不具有根名称的单个树、单个根目录 / 和单个当前目录。

另一个重要差异是路径名的本机表示方式：

- Windows 使用以 null 结尾的 wchar_t 序列，编码为 UTF-16（每个字符一个或两个元素）。

- Posix 使用以 null 结尾的 char 序列，编码为 UTF-8（每个字符一个或多个元素）。

- 类路径的对象以本机形式存储路径名，但支持在此存储形式与多种外部形式之间进行简单转换：

- 以 null 结尾的 char 序列，编码为操作系统偏好的形式。

- 以 null 结尾的 char 序列，编码为 UTF-8。

- 以 null 结尾的 wchar_t 序列，编码为操作系统偏好的形式。

- 以 null 结尾的 char16_t 序列，编码为 UTF-16。

- 以 null 结尾的 char32_t 序列，编码为 UTF-32。

通过使用一个或多个 `codecvt` facet，按需调节这些表示形式之间的相互转换。 如果未指定特定的区域设置对象，则将从全局区域设置获取这些 facet。

另一个差别是每个操作系统允许你用于指定文件或目录访问权限的详细信息：

1. Windows 记录文件是只读还是可写，此属性对于目录没有意义。

1. Posix 记录文件是否可由所有者、所有者组或任何人读取、写入或执行（若为目录则还记录是否可扫描），以及一些其他权限。

两个系统的共同点是通过根名称后施加于路径名的结构。 对于路径名 c:/abc/xyz/def.ext：

- 根名称为 c:。

- 根目录为 /。

- 根路径为 c:/。

- 相对路径为 abc/xyz/def.ext。

- 父路径为 c:/abc/xyz。

- 文件名为 def.ext。

- 主干为 def。

- 扩展名为 .ext。

一个细微的差别是路径名中目录序列之间的 **首选分隔符**。 两个操作系统都允许写入正斜杠 /，但在某些上下文中 Windows 偏好反斜杠 \\。

最后，路径对象的一项重要功能是，当文件名参数为标头 \<fstream> 中定义的类所需时，即可使用这些对象。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="members"></a>成员

### <a name="classes"></a>类

|||
|-|-|
|[directory_entry 类](../standard-library/directory-entry-class.md)|描述 `directory_iterator` 或 `recursive_directory_iterator` 返回的对象，并包含路径。|
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
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|如果目标文件已存在，则与 [copy_file](../standard-library/filesystem-functions.md#copy_file) 一起使用的枚举将决定行为。|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|为目录迭代器指定选项的枚举。|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|文件类型的枚举。|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)||
|[perms](../standard-library/filesystem-enumerations.md#perms)|用于传达权限和权限选项的位掩码类型|

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)
