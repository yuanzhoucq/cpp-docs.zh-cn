---
title: nested_exception 类
ms.date: 11/04/2016
f1_keywords:
- exception/std::bad_exception
helpviewer_keywords:
- bad_exception class
ms.assetid: 5ae2c4ef-c7ad-4469-8a9e-a773e86bb000
ms.openlocfilehash: a568a8d9a3817883656406d63c3dd948539bb385
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268519"
---
# <a name="nestedexception-class"></a>nested_exception 类

此类描述用于多个继承异常。 它捕获当前已处理的异常，并将其存储以供将来使用。

## <a name="syntax"></a>语法

```cpp
class nested_exception {
    public:
        nested_exception();
        nested_exception(const nested_exception&) = default;
        virtual ~nested_exception() = default; // access functions
};
```

## <a name="members"></a>成员

### <a name="operators"></a>运算符

|||
|-|-|
|[operator=](#op_as)||

### <a name="functions"></a>函数

|||
|-|-|
|[rethrow_nested](#rethrow_nested)|将引发存储的异常。|
|[nested_ptr](#nested_ptr)|返回存储的异常。|

### <a name="op_as"></a> 运算符 =

```cpp
nested_exception& operator=(const nested_exception&) = default;
```

### <a name="nested_ptr"></a> nested_ptr

```cpp
exception_ptr nested_ptr() const;
```

#### <a name="return-value"></a>返回值

此捕获的存储的异常`nested_exception`对象。

### <a name="rethrow_nested"></a> rethrow_nested

```cpp
[[noreturn]] void rethrow_nested() const;
```

#### <a name="remarks"></a>备注

如果`nested_ptr()`返回 null 指针，该函数将调用`std::terminate()`。 否则，它将引发所捕获的存储的异常`*this`。

## <a name="requirements"></a>要求

**标头：** \<exception>

**命名空间：** std

## <a name="see-also"></a>请参阅

[exception 类](../standard-library/exception-class.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
