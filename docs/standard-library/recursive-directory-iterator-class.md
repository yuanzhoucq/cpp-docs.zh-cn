---
title: recursive_directory_iterator 类
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 0f9bdc3edd7f5798afaa8d170adc35708a6aafa2
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217618"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator 类

描述一个输入迭代器，该迭代器通过目录中的文件名进行排序，可能以递归方式降序到子目录。 对于迭代器 `X` ，该表达式的 `*X` 计算结果为类的一个对象， `directory_entry` 该对象包装文件名和任何有关其状态的已知信息。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>语法

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>备注

类模板存储：

1. 一个类型为的对象 `stack<pair<directory_iterator, path>>` ，在 `mystack` 此处出于处于阐释的目的调用，该对象表示要进行排序的目录的嵌套

1. 在此处调用的类型的对象 `directory_entry` `myentry` ，它表示目录序列中的当前文件名

1. 一个类型为的对象 **`bool`** ， `no_push` 在此处调用，它记录是否禁用了递归下降到子目录中

1. 一个类型为的对象 `directory_options` ，在 `myoptions` 此处调用，用于记录在构造时建立的选项

类型的默认构造对象 `recursive_directory_entry` 在上有一个序列结尾迭代器 `mystack.top().first` ，并表示序列末迭代器。 例如，给定 `abc` 包含条目 `def` （目录）、 `def/ghi` 和 `jkl` 的目录：

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

将调用具有参数和的 `path("abc/def/ghi")` `path("abc/jkl")` 。 可以通过以下两种方式，通过目录子树限定排序：

1. 仅当构造的 `recursive_directory_iterator` `directory_options` 参数的值为时，才会扫描目录符号链接 `directory_options::follow_directory_symlink` 。

1. 如果调用，则 `disable_recursion_pending` 不会以递归方式扫描在增量过程中遇到的后续目录。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|构造一个 `recursive_directory_iterator`。|

### <a name="member-functions"></a>成员函数

|成员函数|说明|
|-|-|
|[长度](#depth)|返回 `mystack.size() - 1` ，因此 `pval` 在深度为零。|
|[disable_recursion_pending](#disable_recursion_pending)|将存储 **`true`** 在中 `no_push` 。|
|increment|按顺序前进到下一个文件名。|
|[options](#options)|返回 `myoptions`。|
|[弹出](#pop)|返回下一个对象。|
|[recursion_pending](#recursion_pending)|返回 `!no_push`。|

### <a name="operators"></a>运算符

|操作员|描述|
|-|-|
|[operator！ =](#op_neq)|返回 `!(*this == right)`。|
|[operator =](#op_as)|默认成员赋值运算符的行为符合预期。|
|[operator = =](#op_eq)|**`true`** 仅当 **`*this`** 和*权限*都是序列末尾迭代器，或者两者都不是序列的结束迭代器时返回。|
|[操作员](#op_multiply)|返回 `myentry`。|
|[operator->](#op_cast)|返回 `&**this`。|
|[operator + +](#op_increment)|递增 `recursive_directory_iterator` 。|

## <a name="requirements"></a>要求

**标头：**\<filesystem>

**命名空间：** std::tr2::sys

## <a name="recursive_directory_iteratordepth"></a><a name="depth"></a>recursive_directory_iterator：:d epth

返回 `mystack.size() - 1` ，因此 `pval` 在深度为零。

```cpp
int depth() const;
```

## <a name="recursive_directory_iteratordisable_recursion_pending"></a><a name="disable_recursion_pending"></a>recursive_directory_iterator：:d isable_recursion_pending

将存储 **`true`** 在中 `no_push` 。

```cpp
void disable_recursion_pending();
```

## <a name="recursive_directory_iteratorincrement"></a><a name="increment"></a>recursive_directory_iterator：：递增值

按顺序前进到下一个文件名。

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>参数

*欧洲*\
指定的错误代码。

### <a name="remarks"></a>备注

该函数尝试推进到嵌套序列中的下一个文件名。 如果成功，它会将该文件名存储在中 `myentry` ; 否则，它将生成序列末迭代器。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_neq"></a>recursive_directory_iterator：： operator！ =

返回 `!(*this == right)`。

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*然后*\
用于比较的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_as"></a>recursive_directory_iterator：： operator =

默认成员赋值运算符的行为符合预期。

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*recursive_directory_iterator*\
要[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)复制到中的 recursive_directory_iterator `recursive_directory_iterator` 。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_eq"></a>recursive_directory_iterator：： operator = =

**`true`** 仅当 **`*this`** 和*权限*都是序列末尾迭代器，或者两者都不是序列的结束迭代器时返回。

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*然后*\
用于比较的[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="recursive_directory_iteratoroperator"></a><a name="op_multiply"></a>recursive_directory_iterator：： operator *

返回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="recursive_directory_iteratoroperator-"></a><a name="op_cast"></a>recursive_directory_iterator：： operator->

返回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="recursive_directory_iteratoroperator"></a><a name="op_increment"></a>recursive_directory_iterator：： operator + +

递增 `recursive_directory_iterator` 。

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>参数

*整形*\
指定的增量。

### <a name="remarks"></a>备注

第一个成员函数调用 `increment()` ，然后返回 **`*this`** 。 第二个成员函数将创建对象的副本，调用 `increment()` ，然后返回副本。

## <a name="recursive_directory_iteratoroptions"></a><a name="options"></a>recursive_directory_iterator：： options

返回 `myoptions`。

```cpp
directory_options options() const;
```

## <a name="recursive_directory_iteratorpop"></a><a name="pop"></a>recursive_directory_iterator：:p op

返回下一个对象。

```cpp
void pop();
```

### <a name="remarks"></a>备注

如果 `depth() == 0` 对象变成序列结尾迭代器，则为。 否则，该成员函数将终止当前（最深）目录的扫描，并在下一较浅深度继续扫描。

## <a name="recursive_directory_iteratorrecursion_pending"></a><a name="recursion_pending"></a>recursive_directory_iterator：： recursion_pending

返回 `!no_push`。

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iteratorrecursive_directory_iterator"></a><a name="recursive_directory_iterator"></a>recursive_directory_iterator：： recursive_directory_iterator

构造一个 `recursive_directory_iterator`。

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*pval*\
指定的路径。

*error_code*\
指定的错误代码。

*opts*\
指定的目录选项。

*recursive_directory_iterator*\
所构造的 `recursive_directory_iterator` 要作为其副本的 `recursive_directory_iterator`。

### <a name="remarks"></a>备注

第一个构造函数将生成序列末迭代器。 第二个和第三个构造函数将存储 **`false`** 在 `no_push` 和 `directory_options::none` 中 `myoptions` ，然后尝试将*pval*作为目录打开和读取。 如果成功，则它们 `mystack` 将初始化并 `myentry` 指定嵌套序列中的第一个非目录文件名; 否则它们将生成序列末迭代器。

第四个和第五个构造函数的行为与第二个和第三个构造函数的行为相同，只不过它们*首先存储的*是 `myoptions` 。 默认构造函数的行为符合预期。

## <a name="see-also"></a>另请参阅

[标头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[文件系统导航 (C++)](../standard-library/file-system-navigation.md)
