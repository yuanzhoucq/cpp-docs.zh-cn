---
title: filesystem_error 类
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: add1e0da43a44c35f39c96e8d65e36aeea0d3afb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 10/31/2018
ms.locfileid: "50628977"
---
# <a name="filesystemerror-class"></a>filesystem_error 类

所引发以报告低级系统溢出的全部异常的基类。

## <a name="syntax"></a>语法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>备注

此类用作引发报告 \<filesystem> 函数中错误的所有异常的基类。 它将存储类型的对象`string`，称为`mymesg`此处出于阐述目的。 它还存储两个对象的类型`path`，称为`mypval1`和`mypval2`。

### <a name="constructors"></a>构造函数

|构造函数|描述|
|-|-|
|[filesystem_error](#filesystem_error)|构造`filesystem_error`消息。|

### <a name="member-functions"></a>成员函数

|成员函数|描述|
|-|-|
|[path1](#path1)|返回 `mypval1`|
|[path2](#path2)|返回 `mypval2`|
|[什么](#what)|返回一个指向 `NTBS` 的指针。|

## <a name="requirements"></a>要求

**标头：** \<文件系统 >

**命名空间：** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error:: filesystem_error

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

*what_arg*<br/>
指定的消息。

*ec*<br/>
指定的错误代码。

*mypval1*<br/>
进一步指定的消息参数。

*mypval2*<br/>
进一步指定的 messsage 参数。

## <a name="path1"></a> filesystem_error::path1

此成员函数返回 `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> filesystem_error::path2

此成员函数返回 `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> filesystem_error::what

此成员函数返回一个指向`NTBS`最好是从组成`runtime_error::what()`， `system_error::what()`， `mymesg`， `mypval1.native_string()`，并`mypval2.native_string()`。

```cpp
const char *what() const noexcept;
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error 类](../standard-library/system-error-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
