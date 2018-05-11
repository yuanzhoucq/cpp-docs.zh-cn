---
title: directory_iterator 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::directory_iterator
- filesystem/std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::directory_iterator
- filesystem/std::experimental::filesystem::directory_iterator::increment
- filesystem/std::experimental::filesystem::directory_iterator::operator=
- filesystem/std::experimental::filesystem::directory_iterator::operator==
- filesystem/std::experimental::filesystem::directory_iterator::operator!=
- filesystem/std::experimental::filesystem::directory_iterator::operator*
- filesystem/std::experimental::filesystem::directory_iterator::operator-&gt;
- filesystem/std::experimental::filesystem::directory_iterator::operator++
dev_langs:
- C++
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::_Directory_iterator::_Directory_iterator
- std::experimental::filesystem::directory_iterator
- std::experimental::filesystem::directory_iterator::directory_iterator
- std::experimental::filesystem::directory_iterator::increment
- std::experimental::filesystem::directory_iterator::operator=
- std::experimental::filesystem::directory_iterator::operator==
- std::experimental::filesystem::directory_iterator::operator!=
- std::experimental::filesystem::directory_iterator::operator*
- std::experimental::filesystem::directory_iterator::operator-&gt;
- std::experimental::filesystem::directory_iterator::operator++
ms.workload:
- cplusplus
ms.openlocfilehash: b46e4d8fc7b59f8b4919a7e36a85f29f626aa80b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="directoryiterator-class"></a>directory_iterator 类

描述通过目录中的文件名排序的输入迭代器。 对于迭代器 X，表达式 *X 计算到 directory_entry 类对文件名及与其状态有关的任何信息进行包装的对象。

该类存储类型路径的对象（此处出于阐述的目的称为 mydir，它表示要对其进行排序的目录的名称）和类型 directory_entry 的对象（此处称为 myentry，它表示目录序列中的当前文件名）。 类型 directory_entry 的默认构造对象具有一个空的 mydir 路径名称并表示序列末迭代器。

例如，给定具有条目 def 和 ghi 的目录 abc，则代码：

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

将通过参数路径 ("abc/def") 和路径 ("abc/ghi") 调用访问。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>语法

```cpp
class directory_iterator;
```

## <a name="directoryiteratordirectoryiterator"></a>directory_iterator::directory_iterator

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

第一个构造函数将生成序列末迭代器。 第二个和第三个构造函数将 pval 存储在 mydir 中，然后尝试将 mydir 作为目录打开和读取。 如果成功，它们会将目录中的第一个文件名存储在 myentry 中；否则它们将生成序列末迭代器。

默认构造函数的行为符合预期。

## <a name="directoryiteratorincrement"></a>directory_iterator::increment

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

该函数尝试转到目录中的下一个文件名。 如果成功，它会将该文件名存储在 myentry 中；否则它会生成一个序列末迭代器。

## <a name="directoryiteratoroperator"></a>directory_iterator::operator!=

```cpp
bool operator!=(const directory_iterator& right) const;
```

该成员运算符返回 !(*this == right)。

## <a name="directoryiteratoroperator"></a>directory_iterator::operator=

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

默认成员赋值运算符的行为符合预期。

## <a name="directoryiteratoroperator"></a>directory_iterator::operator==

```cpp
bool operator==(const directory_iterator& right) const;
```

仅当 *this 和 right 均为序列末迭代器或均不为序列末迭代器时，此成员运算符才返回 true。

## <a name="directoryiteratoroperator"></a>directory_iterator::operator*

```cpp
const directory_entry& operator*() const;
```

该成员运算符将返回 myentry。

## <a name="directoryiteratoroperator-"></a>directory_iterator::operator->

```cpp
const directory_entry * operator->() const;
```

此成员函数返回 &**this。

## <a name="directoryiteratoroperator"></a>directory_iterator::operator++

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

第一个成员函数调用 increment()，然后返回 *this。 第二个成员函数复制该对象，并调用 increment()，然后返回副本。

## <a name="requirements"></a>要求

**标头：**\<experimental/filesystem>

**命名空间：**std::experimental::filesystem

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[文件系统导航 (C++)](../standard-library/file-system-navigation.md)<br/>
