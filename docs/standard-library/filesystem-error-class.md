---
title: filesystem_error 类
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: c3dbfc080f0a1494950016f42189d932be05b0f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240733"
---
# <a name="filesystemerror-class"></a>filesystem_error 类

所引发以报告低级系统溢出的全部异常的基类。

## <a name="syntax"></a>语法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>备注

此类用作引发报告 \<filesystem> 函数中错误的所有异常的基类。 它将存储类型的对象`string`，称为`mymesg`此处出于阐述目的。 它还存储两个对象的类型`path`，称为`mypval1`和`mypval2`。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[filesystem_error](#filesystem_error)|构造`filesystem_error`消息。|

### <a name="functions"></a>函数

|||
|-|-|
|[path1](#path1)|返回 `mypval1`|
|[path2](#path2)|返回 `mypval2`|
|[what](#what)|返回一个指向 `NTBS` 的指针。|

## <a name="requirements"></a>要求

**标头：** \<文件系统 >

**命名空间：** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error

第一个构造函数构造其消息从*what_arg*并*ec*。 第二个构造函数构造其消息从*pval1*，并将其存储在`mypval1`。 第三个构造函数构造其消息从*pval1*，并将其存储在`mypval1`，并从*pval2*，并将其存储在`mypval2`。

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>参数

*what_arg*\
指定的消息。

*ec*\
指定的错误代码。

*mypval1*\
进一步指定的消息参数。

*mypval2*\
进一步指定的 messsage 参数。

## <a name="path1"></a> path1

此成员函数返回 `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> path2

此成员函数返回 `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> 什么

此成员函数返回一个指向`NTBS`最好是从组成`runtime_error::what()`， `system_error::what()`， `mymesg`， `mypval1.native_string()`，并`mypval2.native_string()`。

```cpp
const char *what() const noexcept;
```
