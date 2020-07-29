---
title: directory_iterator 类
ms.date: 09/10/2018
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
ms.assetid: dca2ecf8-3e69-4644-a83d-705061e10cc8
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
ms.openlocfilehash: a7ccc2a941da079e14092af5b81dc537db4a48c0
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215772"
---
# <a name="directory_iterator-class"></a>directory_iterator 类

描述通过目录中的文件名排序的输入迭代器。 对于迭代器 `X` ，该表达式的 `*X` 计算结果为类的一个对象， `directory_entry` 该对象包装文件名和任何有关其状态的已知信息。

类存储一个类型为的对象 `path` ，此对象 `mydir` 用于处于阐释（表示要排序的目录的名称）和一个类型的对象（ `directory_entry` `myentry` 它表示目录序列中的当前文件名）的目的。 类型的默认构造对象 `directory_entry` 具有空 `mydir` 路径名并表示序列末迭代器。

例如，给定 `abc` 包含条目和的目录 `def` `ghi` ，代码为：

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

将调用 `visit` `path("abc/def")` 和参数和 `path("abc/ghi")` 。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>语法

```cpp
class directory_iterator;
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[directory_iterator](#directory_iterator)|构造通过目录中的文件名进行排序的输入迭代器。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|increment|尝试转到目录中的下一个文件名。|

### <a name="operators"></a>运算符

|操作员|描述|
|-|-|
|[operator！ =](#op_neq)|返回 `!(*this == right)`。|
|[operator =](#op_as)|默认成员赋值运算符的行为符合预期。|
|[operator = =](#op_eq)|**`true`** 仅当 **`*this`** 和*权限*都是序列末尾迭代器，或者两者都不是序列的结束迭代器时返回。|
|[操作员](#op_star)|返回 `myentry`。|
|[operator->](#op_cast)|返回 `&**this`。|
|[operator + +](#op_increment)|调用 `increment()` ，然后返回 **`*this`** 对象的副本，调用 `increment()` ，然后返回副本。|

## <a name="requirements"></a>要求

**标头：**\<experimental/filesystem>

**命名空间：** std::experimental::filesystem

## <a name="directory_iteratordirectory_iterator"></a><a name="directory_iterator"></a>directory_iterator：:d irectory_iterator

第一个构造函数将生成序列末迭代器。 第二个和第三个构造函数将*pval*存储在中 `mydir` ，然后尝试将其作为目录打开和读取 `mydir` 。 如果成功，它们会将中的第一个文件名存储在中 `myentry` ; 否则，它们将生成序列末迭代器。

默认构造函数的行为符合预期。

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*pval*\
存储的文件名路径。

*欧洲*\
状态错误代码。

*directory_iterator*\
存储的对象。

## <a name="directory_iteratorincrement"></a><a name="increment"></a>directory_iterator：：递增值

该函数尝试转到目录中的下一个文件名。 如果成功，它会将该文件名存储在中 `myentry` ; 否则，它将生成序列末迭代器。

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="directory_iteratoroperator"></a><a name="op_neq"></a>directory_iterator：： operator！ =

该成员运算符将返回 `!(*this == right)`。

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*然后*\
要[directory_iterator](../standard-library/directory-iterator-class.md)与进行比较的 directory_iterator `directory_iterator` 。

## <a name="directory_iteratoroperator"></a><a name="op_as"></a>directory_iterator：： operator =

默认成员赋值运算符的行为符合预期。

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*然后*\
要[directory_iterator](../standard-library/directory-iterator-class.md)复制到中的 directory_iterator `directory_iterator` 。

## <a name="directory_iteratoroperator"></a><a name="op_eq"></a>directory_iterator：： operator = =

**`true`** 仅当 **`*this`** 和*right*均为序列末尾迭代器，或者两者都不是序列的结束迭代器时，成员运算符才返回。

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*然后*\
要[directory_iterator](../standard-library/directory-iterator-class.md)与进行比较的 directory_iterator `directory_iterator` 。

## <a name="directory_iteratoroperator"></a><a name="op_star"></a>directory_iterator：： operator *

该成员运算符将返回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="directory_iteratoroperator-"></a><a name="op_cast"></a>directory_iterator：： operator->

成员函数返回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="directory_iteratoroperator"></a><a name="op_increment"></a>directory_iterator：： operator + +

第一个成员函数调用 `increment()` ，然后返回 **`*this`** 。 第二个成员函数将创建对象的副本，调用 `increment()` ，然后返回副本。

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>参数

*整形*\
增量数。

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[文件系统导航 (C++)](../standard-library/file-system-navigation.md)
