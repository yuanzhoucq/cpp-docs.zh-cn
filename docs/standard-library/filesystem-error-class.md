---
title: filesystem_error 类
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 7bd6b2d3d716ba25999388d44e7bd5a8d0750eb5
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127204"
---
# <a name="filesystem_error-class"></a>filesystem_error 类

所引发以报告低级系统溢出的全部异常的基类。

## <a name="syntax"></a>语法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>备注

此类用作引发报告 \<filesystem> 函数中错误的所有异常的基类。 它存储类型`string`为的对象，出于`mymesg`处于阐释目的，在此处进行调用。 它还存储两个类型`path`的对象，称为`mypval2` `mypval1`和。

## <a name="members"></a>成员

### <a name="constructors"></a>构造函数

|||
|-|-|
|[filesystem_error](#filesystem_error)|`filesystem_error`构造消息。|

### <a name="functions"></a>函数

|||
|-|-|
|[path1](#path1)|返回 `mypval1`|
|[path2](#path2)|返回 `mypval2`|
|[what](#what)|返回一个指向 `NTBS` 的指针。|

## <a name="requirements"></a>要求

**标头：** \<filesystem >

**命名空间：** std::experimental::filesystem

## <a name="filesystem_error"></a>filesystem_error

第一个构造函数从*what_arg*和*ec*构造其消息。 第二个构造函数还从存储在中`mypval1`的 pval1 (构造其消息。 第三个构造函数还从*pval1 (* 中构造其消息，并`mypval1`从其存储在*pval2* `mypval2`中。

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

*欧洲*\
指定的错误代码。

*mypval1*\
进一步指定的消息参数。

*mypval2*\
进一步指定的消息参数。

## <a name="path1"></a>path1

此成员函数返回 `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a>path2

此成员函数返回 `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a>究竟

成员函数`NTBS`返回一个指向的指针，该指针最好`runtime_error::what()`由、 `system_error::what()` `mymesg` `mypval1.native_string()`、、和`mypval2.native_string()`组成。

```cpp
const char *what() const noexcept;
```
