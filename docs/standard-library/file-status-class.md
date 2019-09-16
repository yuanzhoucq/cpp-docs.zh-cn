---
title: file_status 类
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 60ced1f60c811f585928f47c6cfd5e695d0c4085
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457756"
---
# <a name="file_status-class"></a>file_status 类

包装 [file_type](../standard-library/filesystem-enumerations.md#file_type) 和文件 [perms](../standard-library/filesystem-enumerations.md#perms)。

## <a name="syntax"></a>语法

```cpp
class file_status;
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[file_status](#file_status)|构造[file_type](../standard-library/filesystem-enumerations.md#file_type)和文件[perms](../standard-library/filesystem-enumerations.md#perms)的包装。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[type](#type)|获取或设置 `file_type`。|
|[permissions](#permissions)|获取或设置文件权限。|

### <a name="operators"></a>运算符

|运算符|描述|
|-|-|
|[operator=](#op_as)|默认成员赋值运算符的行为符合预期。|

## <a name="requirements"></a>要求

**标头：** \<filesystem >

**命名空间：** std：：实验：： filesystem，std：：实验：： filesystem

## <a name="file_status"></a>file_status::file_status

构造[file_type](../standard-library/filesystem-enumerations.md#file_type)和文件[perms](../standard-library/filesystem-enumerations.md#perms)的包装。

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>参数

*ftype*\
指定`file_type`，则默认`file_type::none`为。

*掩盖*\
指定的`perms`文件，默认`perms::unknown`为。

*file_status*\
存储的对象。

## <a name="op_as"></a>file_status：： operator =

默认成员赋值运算符的行为符合预期。

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>参数

*file_status*\
要复制到 `file_status` 中的 [file_status](../standard-library/file-status-class.md)。

## <a name="type"></a>类别

获取或设置 `file_type`。

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>参数

*ftype*\
已指定 `file_type`。

## <a name="permissions"></a>访问

获取或设置文件权限。

使用 setter 创建文件`readonly`或删除该`readonly`属性。

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>参数

*掩盖*\
已指定 `perms`。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)\
[path 类](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
