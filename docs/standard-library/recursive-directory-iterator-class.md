---
title: recursive_directory_iterator 类
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: 52e6f738aa226dba26bae0cf6e97cd18d107d677
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 04/23/2019
ms.locfileid: "62370122"
---
# <a name="recursivedirectoryiterator-class"></a>recursive_directory_iterator 类

描述输入迭代器，它通过在目录中，文件名可能降序到子目录以递归方式。 迭代器`X`，表达式`*X`的计算结果为类的对象`directory_entry`文件名和有关其状态的任何包装。

有关详细信息和代码示例，请参阅[文件系统导航 (C++)](../standard-library/file-system-navigation.md)。

## <a name="syntax"></a>语法

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>备注

模板类存储以下内容：

1. 类型的对象`stack<pair<directory_iterator, path>>`，称为`mystack`此处出于阐述，表示要进行序列化的目录的嵌套

1. 类型的对象`directory_entry`调用`myentry`此处，它表示目录序列中的当前文件名

1. 类型的对象**bool**称为`no_push`此处记录是否禁用递归下降到子目录

1. 类型的对象`directory_options`，称为`myoptions`此处记录在构造时建立的选项

类型的默认构造对象`recursive_directory_entry`具有一个序列末迭代器，在`mystack.top().first`和表示序列末迭代器。 例如，给定的目录`abc`与条目`def`（目录）， `def/ghi`，和`jkl`，代码：

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

使用参数将调用访问`path("abc/def/ghi")`和`path("abc/jkl")`。 您可以有资格通过目录子树中两种方式序列化：

1. 仅当构造，则会扫描目录符号链接`recursive_directory_iterator`与`directory_options`自变量的值是`directory_options::follow_directory_symlink`。

1. 如果调用`disable_recursion_pending`则增量过程中遇到的后续目录，不会以递归方式扫描。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|构造一个 `recursive_directory_iterator`。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[depth](#depth)|返回`mystack.size() - 1`，因此`pval`深度为零。|
|[disable_recursion_pending](#disable_recursion_pending)|存储 **，则返回 true**中`no_push`。|
|[increment](#increment)|前进到序列中的下一个文件名。|
|[options](#options)|返回 `myoptions`。|
|[pop](#pop)|返回下一个对象。|
|[recursion_pending](#recursion_pending)|返回 `!no_push`。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator!=](#op_neq)|返回 `!(*this == right)`。|
|[operator=](#op_as)|默认成员赋值运算符的行为符合预期。|
|[operator==](#op_eq)|返回 **，则返回 true**仅当这两种`*this`并*右*为序列末迭代器或 both 是否未结束的-为序列末迭代。|
|[operator*](#op_multiply)|返回 `myentry`。|
|[operator->](#op_cast)|返回 `&**this`。|
|[operator++](#op_increment)|增量`recursive_directory_iterator`。|

## <a name="requirements"></a>要求

**标头：** \<文件系统 >

**命名空间：** std::tr2::sys

## <a name="depth"></a> recursive_directory_iterator:: depth

返回`mystack.size() - 1`，因此`pval`深度为零。

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a> recursive_directory_iterator:: disable_recursion_pending

存储 **，则返回 true**中`no_push`。

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a> recursive_directory_iterator:: increment

前进到序列中的下一个文件名。

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>参数

*ec*<br/>
指定的错误代码。

### <a name="remarks"></a>备注

该函数尝试推进到嵌套序列中的下一个文件名。 如果成功，它将该文件名存储在`myentry`; 否则它会生成序列末迭代器。

## <a name="op_neq"></a> recursive_directory_iterator:: operator ！ =

返回 `!(*this == right)`。

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*right*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)进行比较。

## <a name="op_as"></a> recursive_directory_iterator:: operator =

默认成员赋值运算符的行为符合预期。

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>参数

*recursive_directory_iterator*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)复制到`recursive_directory_iterator`。

## <a name="op_eq"></a> recursive_directory_iterator:: operator = =

返回 **，则返回 true**仅当这两种`*this`并*右*为序列末迭代器或 both 是否未结束的-为序列末迭代。

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>参数

*right*<br/>
[Recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md)进行比较。

## <a name="op_multiply"></a> recursive_directory_iterator:: operator *

返回 `myentry`。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a> recursive_directory_iterator::operator->

返回 `&**this`。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a> recursive_directory_iterator:: operator + +

增量`recursive_directory_iterator`。

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>参数

*int*<br/>
指定的增量。

### <a name="remarks"></a>备注

第一个成员函数调用`increment()`，然后返回`*this`。 第二个成员函数生成的对象，调用副本`increment()`，然后返回副本。

## <a name="options"></a> recursive_directory_iterator:: options

返回 `myoptions`。

```cpp
directory_options options() const;
```

## <a name="pop"></a> recursive_directory_iterator:: pop

返回下一个对象。

```cpp
void pop();
```

### <a name="remarks"></a>备注

如果`depth() == 0`对象将成为序列末迭代器。 否则，该成员函数将终止当前（最深）目录的扫描，并在下一较浅深度继续扫描。

## <a name="recursion_pending"></a> recursive_directory_iterator:: recursion_pending

返回 `!no_push`。

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a> recursive_directory_iterator:: recursive_directory_iterator

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

*pval*<br/>
指定的路径。

*error_code*<br/>
指定的错误代码。

*opts*<br/>
指定的目录的选项。

*recursive_directory_iterator*<br/>
所构造的 `recursive_directory_iterator` 要作为其副本的 `recursive_directory_iterator`。

### <a name="remarks"></a>备注

第一个构造函数将生成序列末迭代器。 第二个和第三个构造函数存储**false**中`no_push`并`directory_options::none`中`myoptions`，然后尝试打开并读取*pval*作为目录。 如果成功，则它们将初始化`mystack`和`myentry`指定嵌套序列; 中的第一个非目录文件名否则它们将生成一个序列末迭代器。

第四个和第五个构造函数的行为相同作为第二个和第三，只不过它们首先存储*opts*中`myoptions`。 默认构造函数的行为符合预期。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[文件系统导航 (C++)](../standard-library/file-system-navigation.md)<br/>
