---
title: directory_iterator 类 | Microsoft 文档
ms.custom: ''
ms.date: 09/10/2018
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
ms.openlocfilehash: 09970c0d3cf8771317c93670c0ec7f029e1ace2a
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691583"
---
# <a name="directoryiterator-class"></a>directory_iterator 类

描述通过目录中的文件名排序的输入迭代器。 迭代器`X`，表达式`*X`的计算结果为类的对象`directory_entry`文件名和有关其状态的任何包装。

类存储类型的对象`path`，称为`mydir`在此处阐述，它表示要进行序列化的目录的名称的目的和类型的对象供`directory_entry`调用`myentry`这里，表示当前目录序列中的文件名。 类型的默认构造对象`directory_entry`具有空`mydir`路径名，表示序列末迭代器。

例如，给定的目录`abc`与条目`def`和`ghi`，代码：

`for (directory_iterator next(path("abc")), end; next != end; ++next)     visit(next->path());`

将调用`visit`使用参数`path("abc/def")`和`path("abc/ghi")`。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>语法

```cpp
class directory_iterator;
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[directory_iterator](#directory_iterator)|构造一个目录中的文件名排序的输入迭代器。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[增量](#increment)|尝试转到目录中的下一个文件名。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](#op_neq)|返回 `!(*this == right)`。|
|[operator=](#op_as)|默认成员赋值运算符的行为符合预期。|
|[operator==](#op_eq)|返回 **，则返回 true**仅当这两种`*this`并*右*为序列末迭代器或 both 是否未结束的-为序列末迭代。|
|[operator*](#op_star)|返回 `myentry`。|
|[operator->](#op_cast)|返回 `&**this`。|
|[operator++](#op_increment)|调用`increment()`，然后返回`*this`，或创建的对象，调用副本`increment()`，然后返回副本。|

## <a name="requirements"></a>要求

**标头：**\<experimental/filesystem>

**命名空间：** std::experimental::filesystem

## <a name="directory_iterator"></a> directory_iterator:: directory_iterator

第一个构造函数将生成序列末迭代器。 第二个和第三个构造函数存储*pval*中`mydir`，然后尝试打开并读取`mydir`作为目录。 如果成功，它们将存储的第一个文件名的目录中`myentry`; 否则它们将生成一个序列末迭代器。

默认构造函数的行为符合预期。

```cpp
directory_iterator() noexcept;
explicit directory_iterator(const path& pval);

directory_iterator(const path& pval, error_code& ec) noexcept;
directory_iterator(const directory_iterator&) = default;
directory_iterator(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*pval*<br/>
存储的文件名称路径。

*ec*<br/>
状态错误代码。 

*directory_iterator*<br/>
存储的对象。

## <a name="increment"></a> directory_iterator:: increment

该函数尝试转到目录中的下一个文件名。 如果成功，它将该文件名存储在`myentry`; 否则它会生成序列末迭代器。

```cpp
directory_iterator& increment(error_code& ec) noexcept;
```

## <a name="op_neq"></a> directory_iterator:: operator ！ =

该成员运算符将返回 `!(*this == right)`。

```cpp
bool operator!=(const directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md)要进行比较的`directory_iterator`。

## <a name="op_as"></a> directory_iterator:: operator =

默认成员赋值运算符的行为符合预期。

```cpp
directory_iterator& operator=(const directory_iterator&) = default;
directory_iterator& operator=(directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md)复制到`directory_iterator`。

## <a name="op_eq"></a> directory_iterator:: operator = =

成员运算符将返回 **，则返回 true**仅当这两种`*this`并*右*为序列末迭代器或 both 是否未结束的-为序列末迭代。

```cpp
bool operator==(const directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*right*<br/>
[Directory_iterator](../standard-library/directory-iterator-class.md)要进行比较的`directory_iterator`。

## <a name="op_star"></a> directory_iterator:: operator *

该成员运算符将返回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> directory_iterator:: operator->

成员函数返回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> directory_iterator:: operator + +

第一个成员函数调用`increment()`，然后返回`*this`。 第二个成员函数生成的对象，调用副本`increment()`，然后返回副本。

```cpp
directory_iterator& operator++();
directory_iterator& operator++(int);
```

### <a name="parameters"></a>参数

*int*<br/>
增量数。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[文件系统导航 (C++)](../standard-library/file-system-navigation.md)<br/>
