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
ms.openlocfilehash: 8c6dcce3de32c7e25d2489cb508454dff500a1a6
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68454417"
---
# <a name="directory_iterator-class"></a>directory_iterator 类

描述通过目录中的文件名排序的输入迭代器。 对于迭代器`X`，该表达式`*X`的计算结果为类`directory_entry`的一个对象，该对象包装文件名和任何有关其状态的已知信息。

`path`类存储一个类型为的对象`mydir` ，在此处为处于阐释（表示要排序的目录的名称）和`myentry`一个类型`directory_entry`的对象（表示当前目录序列中的文件名。 类型`directory_entry`的默认构造对象具有空`mydir`路径名并表示序列末迭代器。

例如，给定包含条目`abc` `def`和`ghi`的目录，代码为：

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

将调用`visit`和参数`path("abc/def")`和`path("abc/ghi")`。

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

|成员函数|描述|
|-|-|
|[increment](#increment)|尝试转到目录中的下一个文件名。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](#op_neq)|返回 `!(*this == right)`。|
|[operator=](#op_as)|默认成员赋值运算符的行为符合预期。|
|[operator==](#op_eq)|仅当`*this`和*right*均为序列末尾迭代器，或者两者都不是序列的结束迭代器时，才返回 true。|
|[operator*](#op_star)|返回 `myentry`。|
|[operator->](#op_cast)|返回 `&**this`。|
|[operator++](#op_increment)|调用`increment()`，然后返回`*this`对象的副本，调用`increment()`，然后返回副本。|

## <a name="requirements"></a>要求

**标头：** \<experimental/filesystem>

**命名空间：** std::experimental::filesystem

## <a name="directory_iterator"></a>directory_iterator：:d irectory_iterator

第一个构造函数将生成序列末迭代器。 第二个和第三个构造`mydir`函数将 pval 存储在中， `mydir`然后尝试将其作为目录打开和读取。 如果成功，它们会将中的第一个文件名存储`myentry`在中; 否则，它们将生成序列末迭代器。

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

## <a name="increment"></a>directory_iterator：：递增

该函数尝试转到目录中的下一个文件名。 如果成功，它会将该文件名`myentry`存储在中; 否则，它将生成序列末迭代器。

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a>directory_iterator：： operator！ =

该成员运算符将返回 `!(*this == right)`。

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*然后*\
要与`directory_iterator`进行比较的 [directory_iterator](../standard-library/directory-iterator-class.md)。

## <a name="op_as"></a>directory_iterator：： operator =

默认成员赋值运算符的行为符合预期。

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*然后*\
要复制到`directory_iterator`中的 [directory_iterator](../standard-library/directory-iterator-class.md)。

## <a name="op_eq"></a>directory_iterator：： operator = =

仅当`*this`和*right*均为序列末尾迭代器，或者两者都不是序列的结束迭代器时，成员运算符才返回**true** 。

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*然后*\
要与`directory_iterator`进行比较的 [directory_iterator](../standard-library/directory-iterator-class.md)。

## <a name="op_star"></a>directory_iterator：： operator *

该成员运算符将返回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>directory_iterator：： operator->

成员函数返回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>directory_iterator：： operator + +

第一个成员函数调用`increment()`，然后返回`*this`。 第二个成员函数将创建对象的副本，调用`increment()`，然后返回副本。

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>参数

*整形*\
增量数。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[文件系统导航 (C++)](../standard-library/file-system-navigation.md)
