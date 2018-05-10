---
title: filesystem_error 类 | Microsoft 文档
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
dev_langs:
- C++
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e1acf34f8478bc075b53780f1e48df125c22608b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 05/07/2018
---
# <a name="filesystemerror-class"></a>filesystem_error 类

所引发以报告低级系统溢出的全部异常的基类。

## <a name="syntax"></a>语法

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>备注

此类用作引发报告 \<filesystem> 函数中错误的所有异常的基类。 它存储类型为 string 的对象，出于阐释目的将其称为 mymesg。 它还存储两个 path 类型的对象，称为 mypval1 和 mypval2。

## <a name="filesystemerrorfilesystemerror"></a>filesystem_error::filesystem_error

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

第一个构造函数从 what_arg 和 ec 构造其消息。 第二个构造函数从 pval1（存储在 mypval1 中）构造其消息。 第三个构造函数从 pval1（存储在 mypval1）和 pval2（存储在 mypval2 中）构造其消息。

## <a name="filesystemerrorpath1"></a>filesystem_error::path1

```cpp
const path& path1() const noexcept;
```

此成员函数返回 mypval1

## <a name="filesystemerrorpath2"></a>filesystem_error::path2

```cpp
const path& path2() const noexcept;
```

此成员函数返回 mypval2

## <a name="filesystemerrorwhat"></a>filesystem_error::what

```cpp
const char *what() const noexcept;
```

此成员函数返回指向 NTBS 的指针，最好是由 runtime_error::what()、system_error::what()、mymesg、mypval1.native_string() 和 mypval2.native_string() 组成。

## <a name="requirements"></a>要求

**标头：** \<文件系统 >

**命名空间：**std::experimental::filesystem

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[system_error 类](../standard-library/system-error-class.md)<br/>
[\<filesystem>](../standard-library/filesystem.md)<br/>
[\<exception>](../standard-library/exception.md)<br/>
