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
ms.openlocfilehash: 81ce4ecc1673087db8e985f94e297798dd712a6e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630615"
---
# <a name="filestatus-class"></a>file_status 类

包装 [file_type](../standard-library/filesystem-enumerations.md#file_type) 和文件 [perms](../standard-library/filesystem-enumerations.md#perms)。

## <a name="syntax"></a>语法

```cpp
class file_status;
```

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[file_status](#file_status)|构造的包装器[file_type](../standard-library/filesystem-enumerations.md#file_type)和文件[perms](../standard-library/filesystem-enumerations.md#perms)。|

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

**标头：** \<文件系统 >

**Namespace:** std::experimental::filesystem、 std::experimental::filesystem

## <a name="file_status"></a> file_status:: file_status

构造的包装器[file_type](../standard-library/filesystem-enumerations.md#file_type)和文件[perms](../standard-library/filesystem-enumerations.md#perms)。

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>参数

*ftype*<br/>
指定`file_type`，默认为`file_type::none`。

*掩码*<br/>
指定的文件`perms`，默认为`perms::unknown`。

*file_status*<br/>
存储的对象。

## <a name="op_as"></a> file_status::operator =

默认成员赋值运算符的行为符合预期。

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>参数

*file_status*<br/>
[File_status](../standard-library/file-status-class.md)复制到`file_status`。

## <a name="type"></a> 类型

获取或设置 `file_type`。

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>参数

*ftype*<br/>
已指定 `file_type`。

## <a name="permissions"></a> 权限

获取或设置文件权限。

使用资源库创建的文件`readonly`或删除`readonly`属性。

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>参数

*掩码*<br/>
已指定 `perms`。

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[path 类](../standard-library/path-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
