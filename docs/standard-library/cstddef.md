---
title: '&lt;cstddef&gt;'
ms.date: 11/04/2016
f1_keywords:
- <cstddef>
helpviewer_keywords:
- cstddef header
ms.assetid: be8d1e39-5974-41ee-b41d-eafa6c82ffce
ms.openlocfilehash: 15d13a3af35cb41950df8aeba0c86d779e701ddb
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 07/16/2019
ms.locfileid: "68244447"
---
# <a name="ltcstddefgt"></a>&lt;cstddef&gt;

包含 C 标准库标头\<stddef.h > 并将关联的名称到添加`std`命名空间。 包括此标头中声明 C 标准库标头中使用外部链接声明的名称将确保`std`命名空间。

> [!NOTE]
> \<cstddef > 包括类型**字节**且不会包括类型**wchar_t**。

## <a name="syntax"></a>语法

```cpp
#include <cstddef>
```

## <a name="namespace-and-macros"></a>Namespace 和宏

```cpp
namespace std {
    using ptrdiff_t = see definition;
    using size_t = see definition;
    using max_align_t = see definition;
    using nullptr_t = decltype(nullptr);
}

#define NULL  // an implementation-defined null pointer constant
#define offsetof(type, member-designator)
```

### <a name="parameters"></a>参数

*ptrdiff_t*\
实现定义带符号整数类型，可存储两个下标的数组对象中的差异。

*size_t*\
实现定义无符号的整数类型的大小正好能容纳的大小以字节为单位的任何对象。

*这些*\
其对齐要求是至少一样大，每个标量类型，并在每个上下文中支持的对齐需求的 POD 类型。

*nullptr_t*\
类型的同义词**nullptr**表达式。 尽管**nullptr**不能采用地址，另一个*nullptr_t*可将是左值的对象。

## <a name="byte-class"></a>字节类

```cpp
enum class byte : unsigned char {};

template <class IntType>
    constexpr byte& operator<<=(byte& b, IntType shift) noexcept;
    constexpr byte operator<<(byte b, IntType shift) noexcept;
    constexpr byte& operator>>=(byte& b, IntType shift) noexcept;
    constexpr byte operator>>(byte b, IntType shift) noexcept;

constexpr byte& operator|=(byte& left, byte right) noexcept;
constexpr byte operator|(byte left, byte right) noexcept;
constexpr byte& operator&=(byte& left, byte right) noexcept;
constexpr byte operator&(byte left, byte right) noexcept;
constexpr byte& operator^=(byte& left, byte right) noexcept;
constexpr byte operator^(byte left, byte right) noexcept;
constexpr byte operator~(byte b) noexcept;

template <class IntType>
    IntType to_integer(byte b) noexcept;
```

## <a name="see-also"></a>请参阅

[头文件引用](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 标准库概述](../standard-library/cpp-standard-library-overview.md)<br/>
[C++ 标准库中的线程安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
